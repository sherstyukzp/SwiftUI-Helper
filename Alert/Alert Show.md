Tag: #Alert #Button

---
## Описание:


---
## Скриншот:
![[7Show-Alert.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
        @State var isAlert = false

        let primaryButton = Alert.Button.default(Text("Yes")) {
            print("Yes, I'm a student.")
        }
    
        let secondaryButton = Alert.Button.destructive(Text("No")) {
            print("No, I'm not a student.")
        }
        
        var alert: Alert {
            Alert(title: Text("Question"),
                  message: Text("Are you a student?"),
                  primaryButton: primaryButton,
                  secondaryButton: secondaryButton)
        }

        var body: some View {
            VStack {
                Button("Alert Sheet") {
                    self.isAlert = true
                }
            }.alert(isPresented: $isAlert, content: {
                alert
            })

        }
    }

```

---
## Связаные ссылки:
[[VStack]]
[[Button]]

---
## Обратные ссылки:
[[Alert]]
