https://stackoverflow.com/questions/56726663/how-to-add-a-textfield-to-alert-in-swiftui


       func addListAlertView(){
              let alert = UIAlertController(title: "Create a New List", message: "", preferredStyle: .alert)


              alert.addTextField{(pass) in
                  pass.placeholder = "Enter the name of the new list"
              }

              let create = UIAlertAction(title: "Create", style: .default){_ in

                  if let name = alert.textFields?[0].text{
                      //if no input
                      if name.isEmpty{
                          errorAlertView(title: "Cannot Create the List", message: "The name of list cannot be empty")
                      }
                      //if already exits
                      else if plantListsEnts.contains(where: {$0.listName == name}){

                          errorAlertView(title: "Cannot Create the List", message: "This list already exists")

                      }
                      //if valid list name
                      else{
                          withAnimation {
                              let newList = PlantListEnt(context: viewContext)
                              newList.listName = name
                              saveEntity()
                          }
                      }
                  }else{
                      //error -- this shouldn't happen
                  }

              }

              let cancel = UIAlertAction(title: "Cancel", style: .destructive)

              alert.addAction(cancel)

              alert.addAction(create)

              UIApplication.shared.windows.first?.rootViewController?.present(alert, animated: true)

          }

          func errorAlertView(title:String, message:String){
              let alert = UIAlertController(title: title, message: message, preferredStyle: .alert)

              let dismiss = UIAlertAction(title: "Dismiss", style: .destructive)

              alert.addAction(dismiss)

              UIApplication.shared.windows.first?.rootViewController?.present(alert, animated: true)

          }
