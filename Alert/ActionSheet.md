Tag: #Alert #ActionSheet

---
## Описание:


---
## Скриншот:
![[8Show-ActionSheet.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
    @State var isPresented = false

    var myActionSheet: ActionSheet {
        ActionSheet(title: Text("Information"),
            message: Text("What's your favorite?"),
            buttons: [
                .default(Text("Fishing")) {
                    print("---I like fishing")
                },
                .destructive(Text("Hunting")) {
                    print("---I like hunting")
                },
                .cancel({
                    print("---Nothing")
                })
            ]
        )
    }

    var body: some View {
        VStack {
            Button("Show action sheet") {
                self.isPresented = true
            }
        }
        .actionSheet(isPresented: $isPresented, content: {
            myActionSheet
        })
    }
}
	
```

---
## Связаные ссылки:
[[VStack]]
[[Button]]
[[Text]]

---
## Обратные ссылки:
[[Alert]]