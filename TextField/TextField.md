Tag: #TextField #padding #frame #textFieldStyle

---
## Описание:
TextField используется для добавления обычного поля ввода, которое часто используется в качестве ввода текста.

---
## Скриншот
![[Field.png]]

---
## Код:

``` swift
TextField(self.$name, placeholder: self.nameText, onEditingChanged: { changed in
    print("onEditing: \\(changed)")
}) {
    print("userName: \\(self.name)")
    self.endEditing(true)
}}
.padding(10)
.frame(height: 50)
.textFieldStyle(RoundedBorderTextFieldStyle())
.padding(EdgeInsets(top: 0, leading: 20, bottom: 0, trailing: 20))
```

---
## Связаные ссылки:
[[TextField - Начало]]
[[Безопасный TextField]]
[[Валидация данных]]
[[TextField лимит на ввод]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]