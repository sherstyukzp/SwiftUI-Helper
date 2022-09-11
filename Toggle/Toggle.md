Tag: #Toggle #Text 

---
## Описание:
Элемент управления, который переключается между состояниями включения и выключения.

---
## Скриншот
![[Toggle.png]]

---
## Код:

``` swift
Toggle(isOn: $isOn) {
    Text("State: \\(self.isOn \== true ? "Open":"open")")
}.padding(20)

```

---
## Связаные ссылки:
[[Toggle истинное и ложное состояние]]
[[ToggleVisibility]]


---
## Обратные ссылки:
[[01 SwiftUI Helper]]