Tag: #Safary #Button #List  #Link 

---
## Описание:
SwiftUI предоставляет нам специальное представление ссылки, которое выглядит как кнопка, но при нажатии открывает URL-адрес в Safari. Его достаточно просто использовать - просто дайте ему название для кнопки и целевой URL, который будет отображаться, например:

---
## Скриншот:


---
## Код:

``` swift

Link("Learn SwiftUI", destination: URL(string: "https://www.hackingwithswift.com/quick-start/swiftui")!)

```

Поскольку это просто текстовая ссылка, вы можете настроить его шрифтом, цвет и более:

```swift

Link("Visit Apple", destination: URL(string: "https://www.apple.com")!)
    .font(.title)
    .foregroundColor(.red)
	
```

И если вы предпочитаете создать свой собственный вид, а не просто использовать текст, вы тоже можете сделать это:

```swift

Link(destination: URL(string: "https://www.apple.com")!) {
    Image(systemName: "link.circle.fill")
        .font(.largeTitle)
}

```

В качестве альтернативы вы можете открыть URL-адрес из кода с помощью клавиши среды OpenURL, как это:

```swift

struct ContentView: View {
    @Environment(\.openURL) var openURL

    var body: some View {
        Button("Visit Apple") {
            openURL(URL(string: "https://www.apple.com")!)
        }
    }
}

```


---
## Связаные ссылки:
[[List]]
[[Button]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]