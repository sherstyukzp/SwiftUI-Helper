Tag: #LinearGradien #Gradient #Text #foregroundColor #background #font

---
## Описание:


---
## Скриншот:
![[33GradientLinear.png]]

---
## Код:

``` swift
Text("SwifUI Gradient")
    .font(.system(size: 36))
    .padding()
    .foregroundColor(.white)
    .background(LinearGradient(gradient: Gradient(colors: \[.orange, .red, .purple\]), startPoint: .topLeading, endPoint: .bottomTrailing))

}

```

---
## Связаные ссылки:
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]