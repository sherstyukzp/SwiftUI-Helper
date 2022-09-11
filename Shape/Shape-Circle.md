Tag: #Shape #Circle #VStack #ZStack #frame #Rectangle #Color #Rectangle #scaleEffect #fill

---
## Описание:


---
## Скриншот:
![[30Shape-Circle.png]]

---
## Код:

``` swift
VStack{
    Circle()
    Circle()
	.fill(Color.orange)
	.frame(width: 200, height: 200)
    ZStack {
       Circle().fill(Color.purple)
       Circle().fill(Color.yellow).scaleEffect(0.8)
       Circle().fill(Color.orange).scaleEffect(0.6)
    }
    Rectangle()
    Rectangle()
	.fill(Color.orange)
	.frame(width: 200, height: 200)
    ZStack {
       Rectangle().fill(Color.purple)
	.frame(width: 300, height: 200)

       Rectangle().fill(Color.yellow)
	.frame(width: 300, height: 200)
	.scaleEffect(0.8)

       Rectangle()
	.fill(Color.orange)
	.frame(width: 300, height: 200)
	.scaleEffect(0.6)
    }
}

```

---
## Связаные ссылки:
[[VStack]]
[[ZStack]]


---
## Обратные ссылки:
[[01 SwiftUI Helper]]