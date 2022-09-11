Tag: #List #Text #navigationBarTitle

---
## Описание:
Контейнер списка списка для отображения списка данных.

---
## Скриншот:
![[List.png]]

---
## Код:

``` swift
List(0..<5) { item in
    Text("Hello World !")
}.navigationBarTitle(Text("List"), displayMode: .large)

```

---
## Связаные ссылки:
[[List-Delete]]
[[List-Move]]
[[List-DeleteAndMove]]
[[ForEach]]
[[ScrollView]]
[[NavigationBarTitle]]

---
## Обратные ссылки:

[[01 SwiftUI Helper]]