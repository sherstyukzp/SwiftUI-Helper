Tag: #sheet #ActionSheet #VStack #Identifiable #enum #Button #switch

---
## Описание:
Код показывает как можно испоользовать несколько sheet

---
## Скриншот:


---
## Код:

``` swift

enum ActiveSheet: Identifiable {
    case first, second
    
    var id: Int {
        hashValue
    }
}

struct YourView: View {
    @State var activeSheet: ActiveSheet?

    var body: some View {
        VStack {
            Button {
                activeSheet = .first
            } label: {
                Text("Activate first sheet")
            }

            Button {
                activeSheet = .second
            } label: {
                Text("Activate second sheet")
            }
        }
        .sheet(item: $activeSheet) { item in
            switch item {
            case .first:
                FirstView()
            case .second:
                SecondView()
            }
        }
    }
}


```

---
## Связаные ссылки:
[[Button]]
[[VStack]]
[[Text]]

https://developer.apple.com/documentation/swiftui/view/sheet(item:ondismiss:content:)

---
## Обратные ссылки:
[[ActionSheet]]
[[01 SwiftUI Helper]]