Tag: #onAppear #onDisappear #Text #onTapGesture

---
## Описание:


---
## Скриншот:
![[6onAppear-onDisappear.png]]

---
## Код:

``` swift

struct DetailView: View {
    var body: some View {
        Text("Detail")
        .onAppear {
            print("DetailView appeared!")
        }.onDisappear {
            print("DetailView disappeared!")
        }
    }
}

struct ContentView : View {
    
    @State private var isPresented = false
    
    var body: some View
    {
        Text("Show Detail > ").sheet(isPresented: $isPresented, content: {
            DetailView()
        }).onTapGesture {
            self.isPresented = true
        }.onDisappear {
            print("ContentView disappeared!")
        }.onAppear {
            print("ContentView appeared!")
        }
    }
}

```

---
## Связаные ссылки:
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]
