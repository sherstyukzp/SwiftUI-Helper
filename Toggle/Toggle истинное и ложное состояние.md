Tag: #Toggle #Text

---
## Описание:
Переключатель позволяет пользователям перемещаться между истинным и ложным состояниями

---
## Скриншот:
![[1 5.png]]

---
## Код:

``` swift
@State var isShowing = true //state

Toggle(isOn: $isShowing) {
    Text("Hello World")
}.padding()
```

---
## Связаные ссылки:
[[Text]]

---
## Обратные ссылки:
[[Toggle]]