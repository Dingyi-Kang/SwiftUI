This is the excellent tutorial: https://www.youtube.com/watch?v=vL0w3kvng0o

### use isActive:
<img width="561" alt="image" src="https://github.com/Dingyi-Kang/SwiftUI/assets/81428296/8103eddb-284c-438e-b2c3-38d7531fb7b1">


### use tag:
<img width="569" alt="image" src="https://github.com/Dingyi-Kang/SwiftUI/assets/81428296/32bfade3-4446-46a2-a0a3-cd2f22e34ef6">


## Another good turoial: https://www.hackingwithswift.com/quick-start/swiftui/how-to-use-programmatic-navigation-in-swiftui
#### There are two approaches to programmatic navigation: the newer, more powerful option available from iOS 16 and later, or the older, simpler option available available in earlier releases.

<img width="863" alt="image" src="https://github.com/Dingyi-Kang/SwiftUI/assets/81428296/3f7e18ef-70d2-4bb1-b0ae-498ee3ae7bf9">
<img width="906" alt="image" src="https://github.com/Dingyi-Kang/SwiftUI/assets/81428296/90844d0f-9e4b-4a8d-be16-c5527a3053b8">
<img width="879" alt="image" src="https://github.com/Dingyi-Kang/SwiftUI/assets/81428296/35eeb363-a7e6-4130-9ebd-2513b77f358f">
### important
<img width="878" alt="image" src="https://github.com/Dingyi-Kang/SwiftUI/assets/81428296/cd5c1bc0-68f0-4852-8fb5-046ce26d8cc8">

    struct ContentView: View {
        @State private var selection: String? = nil

        var body: some View {
            NavigationView {
                VStack {
                    NavigationLink(destination: Text("View A"), tag: "A", selection: $selection) { EmptyView() }
                    NavigationLink(destination: Text("View B"), tag: "B", selection: $selection) { EmptyView() }

                    Button("Tap to show A") {
                        selection = "A"
                    }

                    Button("Tap to show B") {
                        selection = "B"
                    }
                }
                .navigationTitle("Navigation")
            }
        }
    }
