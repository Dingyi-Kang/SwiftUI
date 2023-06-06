## Use positioning, don't use padding to position your components whcih may cause weird behavior

    struct CardView:View{
        let geo:GeometryProxy
        let colorStr:String
        let text:String
        let imageName:String
        var body: some View{

            ZStack(alignment: .topLeading){
                Color(colorStr)
                    .cornerRadius(8)
                Text(text)
                    .font(.system(size: 20, weight: .bold))
                    .foregroundColor(.white)
                    .padding(.top, 15)
                    .padding(.leading, 20)
                Image(imageName)
                    .frame(width: geo.size.width * 0.5, height: geo.size.height * 0.2)
                    .position(x: colorStr == "lightRed" ? geo.size.width * 0.73 : geo.size.width * 0.7, y: geo.size.height * 0.145)

            }
            .clipped()
            .frame(width: geo.size.width * 0.9, height: geo.size.height * 0.25)
        }
    }



<img width="471" alt="image" src="https://github.com/Dingyi-Kang/SwiftUI/assets/81428296/290141af-2653-4365-a4ea-7574c7639d08">
