https://www.youtube.com/watch?v=wH6CVGHYlJQ

### key is to manipulate the offset with @state variable wisely

      HStack{
                ZStack{
                    HStack{
                        Rectangle().fill(Color("olive"))
                            .frame(width: suggestedListChosed ? 220: 80)
                            .cornerRadius(8)
                            .offset(x:suggestedListChosed ? 80 : 0)
                        Spacer()
                    }
                    
                    HStack(spacing:0){
                        
                        Button {
                            suggestedListChosed = false
                        } label: {
                            HStack{
                                if !suggestedListChosed{
                                    Image(systemName: "list.bullet")
                                        .font(.system(size: 16))
                                        .padding(.leading, 0)
                                        .padding(.trailing, -20)
                                        .foregroundColor(.white)
                                }
                                Text("My lists")
                                    .font(.system(size: 12, weight: .semibold))
                                    .padding(.vertical, 10)
                                    .padding(.leading, 15)
                                    .padding(.trailing, 15)
                                    .foregroundColor(suggestedListChosed ? Color("darkGray"):Color.white)
                                    .cornerRadius(7)
                            }
                            
                        }
                        
                        Button {
                            suggestedListChosed = true
                        } label: {
                            HStack{
                                if suggestedListChosed{
                                    Image(systemName: "list.bullet")
                                        .font(.system(size: 16))
                                        .padding(.leading, 0)
                                        .padding(.trailing, -5)
                                        .foregroundColor(.white)
                                }
                                Text("Suggested Lists")
                                    .font(.system(size: 12, weight: .semibold))
                                    .padding(.vertical, 10)
                                    .padding(.leading, 0)
                                    .padding(.trailing, 10)
                                    .foregroundColor(suggestedListChosed ? Color.white : Color("darkGray"))
                                    .cornerRadius(7)
                            }
                        }
                        
                    }//Hstack
                    //.background(Color("gray2"))
                    //.cornerRadius(8)
                }//Zstack
                .frame(width: 200, height:35)
                .background(Color("gray2"))
                .cornerRadius(8)
                //MARK: This value parameter of the Animation is used to monitor the animation
                //MARK: the animation will be applied only when the monitor value is changed (hence, typically it has to be @State variable)
                //MARK: this can be used to effectily prevent the unwanted animation of the view, like the animation when the whole VC appear
                .animation(Animation.interpolatingSpring(stiffness: 250, damping:30), value:suggestedListChosed)
                .padding(.leading, 20)
                .onAppear() {
                    
                }
                
                
                Spacer()
                
                Button {
                    //filter button tapped
                } label: {
                    HStack(spacing:6){
                        Image("Edit Filters Icon")
                        Text("Edit filters")
                            .font(.system(size: 12, weight: .semibold))
                    }
                    .padding(8)
                    .foregroundColor(.white)
                    .background(Color("olive"))
                    .cornerRadius(8)
                }
                .padding(.trailing, 20)
                
            }//end of HStack
