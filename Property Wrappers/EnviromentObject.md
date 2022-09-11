Tag: #EnviromentObject #NavigationView #VStack #TextField #NavigationLink #Text

---
## Описание:


---
## Скриншот:
![[5EnviromentObject.gif]]

---
## Код:

``` swift
import SwiftUI

class UserModel: ObservableObject {
    @Published var nickName: String = ""
}

struct ContentView : View {
    
    @EnvironmentObject var model : UserModel
    @State var isPresented = false
    
    var body: some View {
        NavigationView {

            VStack{
                TextField("Your nickname", text: $model.nickName)
                .padding()
                
                NavigationLink(destination: DetailView()) {
                    Text("Show Detail")
                }
            }
        }
    }
}

#if DEBUG
struct ContentView_Previews : PreviewProvider {
    static var previews: some View {
        let model = UserModel()
        model.nickName = "Super man"
        return ContentView().environmentObject(model)
    }
}
#endif

```

---
## Связаные ссылки:
[[NavigationView]]
[[VStack]]
[[NavigationLink]]
[[TextField]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]
