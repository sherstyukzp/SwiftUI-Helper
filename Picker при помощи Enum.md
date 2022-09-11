Tag: #Picker #enum 

---
## Описание:
Код показывает работу Picker при помощи Enum

---
## Скриншот:
![[cUpA8.gif]]

---
## Код:

``` swift

enum ReturnTypes : String, CaseIterable {
    case Scaler
    case Vector
    case Matrix
}

```

```swift
struct ContentView: View {
        @State private var returnType: ReturnTypes = .Scaler
        var body: some View {
        NavigationView {
            Form {
                Picker("Return Type:", selection: $returnType) {
                    ForEach(ReturnTypes.allCases, id: \.self) { type in
                        Text(type.rawValue)
                    }
                }
            }
         }
    }
}
```

---
## Связаные ссылки:
[[Использование Picker с формой]]
[[Использование Picker выбора в Form]]

---
## Обратные ссылки:
[[Picker]]