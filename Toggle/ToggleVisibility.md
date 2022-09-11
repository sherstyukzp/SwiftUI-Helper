Tag: #Toggle #VStack #Text #TextField #border

---
## Описание:


---
## Скриншот:
![[8ToggleVisibility.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
    @State var showingPassword \= false
    @State var password \= ""

    var body: some View {
        
        VStack {
            Toggle(isOn: $showingPassword.animation(.spring())) {
                Text("Toggle Password")
            }

            if showingPassword {
                TextField("Password", text: $password)
                    .padding()
                    .border(Color.green, width: 1)
            }
        }
        .padding()
    }
}

```

---
## Связаные ссылки:
[[VStack]]
[[Text]]

---
## Обратные ссылки:
[[Toggle]]