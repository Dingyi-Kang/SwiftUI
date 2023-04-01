before iOS 15, there is no way to customize the seperator Lines' alignment and visibility

In stead we can use ScrollView + VStack + Divider() to have the effect of List view




            ScrollView {
                LazyVStack(alignment: .leading, spacing: 10) {
                    if !suggestedListChosed{
                        Button {
                            //create a new list
                            addListAlertView()
                        } label: {
                            ListCellView(name: "Create a new list", imageName: "plus")
                        }
                        
                    }
                    ForEach(User.currUser.plantLists) { list in
                   
                        Divider()
                        
                        Button {
                            //create a new list
                        } label: {
                            ListCellView(name: "Create a new list", imageName: "plus")
                        }
                        
                    }
                }
                .padding(.horizontal, 20)
                .padding(.top, 20)
            }
