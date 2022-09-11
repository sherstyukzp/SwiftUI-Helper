Tag: #ObservableObject #Alert #TextField #Button #Text

---
## Описание:


---
## Скриншот:
![[4ObjectBinding.gif]]

---
## Код:

``` swift
class UserModel: ObservableObject {
    @Published var nickName: String = ""
}

struct ContentView : View {
    @ObservedObject var model = UserModel()
    @State var isPresented = false

    let dismiss = Alert.Button.default(Text("OK")) {}
    var alert: Alert {
        Alert(title: Text("Your nickname"),
             message: Text("\(self.model.nickName)"),
             dismissButton: dismiss)
    }
    
    var body: some View {
        VStack {
            TextField("Your nickname", text: $model.nickName)
            .padding()
            
            Button(action: {
                self.isPresented = true
            }) {
                Text("Show")
            }.alert(isPresented: $isPresented) { () -> Alert in
                alert
            }
        }
    }
}

```

---
## Связаные ссылки:
[[TextField]]
[[Text]]
[[Button]]
[[Alert]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]