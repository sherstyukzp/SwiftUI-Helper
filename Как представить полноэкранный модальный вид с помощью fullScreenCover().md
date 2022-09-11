Tag: #fullScreenCover #environment 

---
## Описание:
Модификатор SwiftUI fullScreenCover () дает нам стиль представления для тех случаев, когда вы хотите покрыть как можно большую часть экрана, и в коде он работает почти так же, как обычные листы.
Например, при нажатии кнопки будет представлен полноэкранный модальный вид:

---
## Скриншот:


---
## Код:

``` swift

struct ContentView: View {
    @State private var isPresented = false

    var body: some View {
        Button("Present!") {
            self.isPresented.toggle()
        }
        .fullScreenCover(isPresented: $isPresented, content: FullScreenModalView.init)
    }
}

```

Очевидно, вам нужно будет заменить FullScreenModalView вашим собственным примером представления, но для начала достаточно чего-то вроде этого:

```swift
struct FullScreenModalView: View {
    @Environment(\.presentationMode) var presentationMode

    var body: some View {
        VStack {
            Text("This is a modal view")
        }
        .frame(maxWidth: .infinity, maxHeight: .infinity)
        .background(Color.red)
        .edgesIgnoringSafeArea(.all)
        .onTapGesture {
            presentationMode.wrappedValue.dismiss()
        }
    }
}

```


---
## Связаные ссылки:


---
## Обратные ссылки:
[[01 SwiftUI Helper]]