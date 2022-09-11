Tag: #Stepper #Text 

---
## Описание:
Stepper используется для увеличения или уменьшения значения, например:

---
## Скриншот:
![[Stepper.png]]

---
## Код:

``` swift
Stepper(value: $value, step: 2, onEditingChanged: { c in
    print(c)
}) {
    Text("Stepper Value: \\(self.value)")
    }.padding(50)
	
```

---
## Связаные ссылки:
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]


