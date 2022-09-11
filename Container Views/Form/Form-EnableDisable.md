Tag: #Form 

---
## Описание:


---
## Скриншот:
![[15Form-EnableDisable.png]]

---
## Код:

``` swift
struct ContentView : View {

    @State var enableForm = false
    @State var enableNotification = false
    @State var userName = ""
    @State var password = ""

    var body: some View {
        NavigationView {
            Form {
                Toggle(isOn: $enableForm) {
                    Text("Enable Form")
                }
                
                Section(header: Text("Please enter your information:")) {
                    
                    TextField("Username", text: $userName)
                    SecureField("Password", text: $password)
                    Toggle(isOn: $enableNotification) {
                        Text("Enable Notification")
                    }
                }.disabled(enableForm)
                
            }.navigationBarTitle(Text("Profiles"))
        }
    }
}

```

---
## Связаные ссылки:
[[Form]]
[[Toggle]]
[[Container Views/Section]]
[[TextField]]
[[Text]]
[[NavigationBarTitle]]
[[NavigationView]]

---
## Обратные ссылки:
[[Form]]