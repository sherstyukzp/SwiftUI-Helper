Tag: #Text #Button #sheet

---
## Описание:


---
## Скриншот:
![[6Show_Modal.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
    @State var isPresented \= false

    var modalView: some View {
        Text("The Modal View")
            .font(.system(size: 48))
            .bold()
    }

    var body: some View {
        Button("Show Modal View") {
            self.isPresented \= true
        }.sheet(isPresented: $isPresented, content: {
            self.modalView
        })
    }
}

```

---
## Связаные ссылки:
[[Button]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]
