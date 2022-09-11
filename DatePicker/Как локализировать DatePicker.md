Tag: #DatePicker 

---
## Описание:
Локализация DatePicker, по умолчанию все названия месяцев, дней недели на английском

---
## Скриншот:


---
## Код:

``` swift

DatePicker("Please enter date",selection: $wakeUp, in: Date()...)
            .labelsHidden()
            .environment(\.locale, Locale.init(identifier: "pt"))

```

---
## Связаные ссылки:
[[DatePicker]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]