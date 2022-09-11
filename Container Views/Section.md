Tag: #Section #List #ForEach #Text 

---
## Описание:
Section используется для создания содержимого представления верхнего / нижнего колонтитула, которое обычно используется вместе с компонентом List.

---
## Скриншот:
![[Section.png]]

---
## Код:

``` swift
Section(header: Text("I'm header"), footer: Text("I'm footer")) {
    ForEach(0..<3) {
        Text("Hello \\($0)")
    }
}

```

---


## Связаные ссылки:
[[ForEach]]
[[Text]]
[[Section - footer]]
[[Section обзор]]

---
## Обратные ссылки:
[[Container Views]]
[[01 SwiftUI Helper]]