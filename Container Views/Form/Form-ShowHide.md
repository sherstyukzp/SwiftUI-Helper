Tag: #Form #NavigationView #Toggle #Section #navigationBarTitle #TextField #SecureField

---
## Описание:


---
## Скриншот:
![[16Form-ShowHide.png]]

---
## Код:

``` swift
struct ContentView : View {

    @State var showingVisible = false
    @State var userName = ""
    @State var password = ""

    var body: some View {
        NavigationView {
            Form {
                Toggle(isOn: $showingVisible.animation()) {
                    if(showingVisible){
                        Text("Hide Form")
                    }
                    else{
                        Text("Show Form")
                    }
                }
                
                if(showingVisible)
                {
                    Section(header: Text("Please enter your information:")) {
                        
                        TextField("Username", text: $userName)
                        SecureField("Password", text: $password)
                    }
                }
            }.navigationBarTitle(Text("Profiles"))
        }
    }
}

```

---
## Связаные ссылки:
[[NavigationView]]
[[Form]]
[[Toggle]]
[[Container Views/Section]]
[[NavigationBarTitle]]
[[TextField]]
[[SecureField]]

---
## Обратные ссылки:
[[Form]]