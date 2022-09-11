Tag: #VStack #Text #Group #previewDevice #previewDisplayName #font

---
## Описание:


---
## Скриншот:
![[4PreviewDevice.png]]

---
## Код:

``` swift
struct ContentView : View {
    var body: some View {
        VStack{
            Text("Dynamic Type sizes")
                .font(.system(size: 48))
            Text("Dynamic Type sizes")
        }
        
    }
}

#if DEBUG
struct ContentView\_Previews : PreviewProvider {
    static var previews: some View {
        Group {
           ContentView()
              .previewDevice(PreviewDevice(rawValue: "iPhone 8"))
              .previewDisplayName("Device-8")

           ContentView()
              .previewDevice(PreviewDevice(rawValue: "iPhone XS Max"))
              .previewDisplayName("Device-XS Max")
        }
    }
}
#endif

```

---
## Связаные ссылки:
[[Group]]
[[VStack]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]