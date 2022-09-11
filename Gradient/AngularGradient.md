Tag: #AngularGradient #Gradient #Text #font #foregroundColor #background

---
## Описание:


---
## Скриншот:
![[34GradientAngular.png]]

---
## Код:

``` swift
VStack{
    Text("SwifUI Gradient")
    .font(.system(size: 36))
    .padding()
    .foregroundColor(.white)
    .background(AngularGradient(gradient: Gradient(colors: \[.orange, .red, .purple\]), center: UnitPoint(x: 0.5, y: 0.5), angle: Angle.init(degrees: \-45)))

    Text("SwifUI Gradient")
    .font(.system(size: 36))
    .padding()
    .foregroundColor(.white)
    .background(AngularGradient(gradient: Gradient(colors: \[.orange, .red, .purple\]), center: UnitPoint(x: 0.5, y: 0.5), startAngle: Angle.init(degrees: 0), endAngle: Angle.init(degrees: 0)))

}

```


---
## Связаные ссылки:
[[Text]]
[[VStack]]

---
## Обратные ссылки:
[[Gradient]]