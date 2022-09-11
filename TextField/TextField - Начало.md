Tag: #TextField #textFieldStyle

---
## Описание:
Элемент управления, который отображает редактируемый текстовый интерфейс.

---
## Скриншот
![[1 1.png]]

---
## Код:

``` swift
@State var fullName: String = "Joe" //create State

TextField($fullName) // passing it to bind
    .textFieldStyle(.roundedBorder) // adds border
```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[TextField]]