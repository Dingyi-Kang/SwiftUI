

Yes, indeed, you can use an `enum` to manage the navigation state instead of having multiple `Bool` variables. This will be more scalable and easier to manage as your application grows.

Here's how you can do this:

```swift
enum NavigationState {
    case first
    case second
    case third
}

struct ContentView: View {
    @State private var navigationState: NavigationState? = .first

    var body: some View {
        NavigationView {
            VStack {
                NavigationLink(destination: SecondView(navigationState: $navigationState), tag: NavigationState.second, selection: $navigationState) {
                    Text("Go to Second View")
                }
                NavigationLink(destination: ThirdView(), tag: NavigationState.third, selection: $navigationState) {
                    EmptyView()
                }
            }
        }
    }
}

struct SecondView: View {
    @Binding var navigationState: NavigationState?

    var body: some View {
        VStack {
            Button("Go to Third View") {
                navigationState = .third
            }
        }
    }
}

struct ThirdView: View {
    var body: some View {
        Text("Third View")
    }
}
```

In this example, we define an `enum` named `NavigationState` with cases for each of the views. Then, we use a `@State` variable of type `NavigationState?` to control which view is currently being shown. When the button in `SecondView` is pressed, it sets `navigationState` to `.third`, which triggers the `NavigationLink` to `ThirdView` in `ContentView`.
