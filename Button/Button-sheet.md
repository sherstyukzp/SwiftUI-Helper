Tag:#Button #sheet #VStack #Button #Text

---
## Описание:


---
## Скриншот:
![[11Button-sheet.png]]

---
## Код:

``` swift
struct ContentView : View {

    @State var isPresented \= false
    
    var body: some View {
        VStack{
            Button("Show modal") {
                self.isPresented \= true
            }.sheet(isPresented: $isPresented, content: {
                MyDetailView(message: "Modal window")
            })
        }
    }
}

struct MyDetailView: View {
    let message: String

    var body: some View {
        VStack {
            Text(message)
                .font(.largeTitle)
        }
    }
}

```

---
## Связаные ссылки:
[[Text]]
[[Button]]
[[VStack]]

---
## Обратные ссылки:
[[Button]]