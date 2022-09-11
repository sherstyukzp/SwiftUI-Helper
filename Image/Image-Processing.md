Tag: #Image #ScrollView #VStack #blur #brightness #colorInvert #colorMultiply #contrast #hueRotation #saturation #grayscale #luminanceToAlpha

---
## Описание:


---
## Скриншот:
![[16Image-Processing.png]]

---
## Код:

``` swift
ScrollView{
     VStack{
	Image("girlPicture")

	Image("girlPicture")
	    .blur(radius: CGFloat(2))

	Image("girlPicture")
	    .blur(radius: CGFloat(2), opaque: true)

	Image("girlPicture")
	    .brightness(0.2)

	Image("girlPicture")
	    .colorInvert()

	Image("girlPicture")
	    .colorMultiply(Color.yellow)

	Image("girlPicture")
	    .contrast(1.5)
    }

    VStack{
	Image("girlPicture")
	    .hueRotation(Angle.degrees(180))

	Image("girlPicture")
	    .saturation(10)

	Image("girlPicture")
	    .grayscale(5.5)

	Image("girlPicture")
	    .luminanceToAlpha()
    }
}

```

---
## Связаные ссылки:
[[VStack]]
[[ScrollView]]

---
## Обратные ссылки:
[[Image]]
