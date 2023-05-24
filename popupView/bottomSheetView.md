excellent tutorial: https://www.youtube.com/watch?v=wLLDrx_q7Es


### key points in this tutorial:
### 1. how to organize the relationship between bottomSheetView and hostView -- ZStack and a boolean variable
<img width="344" alt="image" src="https://github.com/Dingyi-Kang/SwiftUI/assets/81428296/e4bbc9d8-ee7c-4d22-ae5f-4429e6d4f81d">

### 2. the drag animation and when to recover and when to dismiss -- grad gesture: onChange, onEnd
 
    struct BottomSheetView: View {
        @State var transition:CGSize = .zero
        @State var sheetMode: SheetMode = SheetMode.quarter
        @Binding var show:Bool
        var title:String
        @Binding var chosedSortRule:SortRule

        var body: some View {
            VStack{
                RoundedRectangle(cornerRadius: 3, style: .continuous)
                    .frame(width: 50, height: 5, alignment: .center)
                    .foregroundColor(Color(.systemGray))
                    .padding(10)

                Text(title)
                    .font(.headline)
                    .padding(.top, 5)
                    .padding(.bottom, 20)

                SortSheetContentView(chosedSortRule: $chosedSortRule, show: $show)

                Spacer()
            }
            .frame(maxWidth: .infinity, maxHeight: .infinity)
            .background(Color.white)
            .mask(RoundedRectangle(cornerRadius: 30, style: .continuous))
            .offset(y:transition.height + calculateOffsetY())
            .gesture(
                DragGesture()
                    .onChanged({ value in
                        transition = value.translation
                    })
                    .onEnded({ _ in
                        withAnimation(.interactiveSpring(response: 0.5, dampingFraction: 0.9)) {

                            let yPosition = transition.height + calculateOffsetY()

                            if yPosition > calculateOffsetY() + 130{
                                //dismiss
                                sheetMode = .none
                                show = false
                            }else{
                                //recover
                                transition = .zero
                            }
                        }
                    })
            )
            .ignoresSafeArea(edges:.bottom)
        }

        private func calculateOffsetY() -> CGFloat{

            switch sheetMode{
            case .none:
                return UIScreen.main.bounds.height
            case .quarter:
                return UIScreen.main.bounds.height * 7 / 13
            case .half:
                return UIScreen.main.bounds.height/2
            case .full:
                return 0
            }

        }


    }
