Tag: #TabView 

---
## Описание:
> [!INFO]
Пример полной реализации работы TabView

---
## Скриншот:
![[Screen-Shot-2019-10-21-at-6.43.24-AM-587x1024.png]]
![[Screen-Shot-2019-10-21-at-6.43.12-AM-587x1024.png]]

---
## Код:

``` swift
struct RedView: View {
var body: some View {
Color.red
}
}

struct BlueView: View {
var body: some View {
Color.blue
}
}

TabView {
RedView().tabItem {
Image(systemName: "phone.fill")
Text("First Tab")
}

BlueView()
.tabItem {
Image(systemName: "tv.fill")
Text("Second Tab")
}
}

```

---
## Связанные ссылки:
[[TabView]]
[[Image]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]