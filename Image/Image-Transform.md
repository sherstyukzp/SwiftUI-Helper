Tag: #Image #VStack #scaleEffect #rotationEffect #rotation3DEffect #UnitPoint

---
## Описание:


---
## Скриншот:
![[19Image-Transform.png]]

---
## Код:

``` swift
ScrollView{
            
    VStack{
	Image("girlPicture")
	    .scaleEffect(0.8)

	Image("girlPicture")
	    .scaleEffect(CGSize(width: 1.2, height: 1))

	Image("girlPicture")
	    .scaleEffect(x: 1.5, y: 1, anchor: UnitPoint.bottomLeading)
    }

     VStack{

	Image("girlPicture")
	     .rotationEffect(Angle.init(degrees: 90))

	Image("girlPicture")
	    .rotationEffect(Angle.init(degrees: 30), anchor: UnitPoint.init(x: 0, y: 0))

	Image("girlPicture")
	    .rotation3DEffect(Angle.init(degrees: 30), axis: (x: CGFloat(0.1), y: CGFloat(0.1), z: CGFloat(0)))

    }
}

```

---
## Связаные ссылки:
[[ScrollView]]
[[VStack]]

---
## Обратные ссылки:
[[Image]]