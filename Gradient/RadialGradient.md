Tag: #Gradient #RadialGradient #foregroundColor #background #Text 

---
## Описание:


---
## Скриншот:
![[35GradientRadial.png]]

---
## Код:

``` swift
Text("SwifUI Gradient")
    .font(.system(size: 36))
    .padding()
    .foregroundColor(.white)
    .background(RadialGradient(gradient: Gradient(colors: \[.orange, .red, .purple\]), center: .init(x: 0.5, y: 0.5), startRadius: CGFloat(10), endRadius: CGFloat(120)))

}

```

---
## Связаные ссылки:
[[Text]]

---
## Обратные ссылки:
[[Gradient]]