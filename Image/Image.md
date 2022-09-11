Tag: #Image #ScrollView  #VStack 

---
## Описание:


---
## Скриншот:
![[15Image-Style.png]]

---
## Код:

``` swift 
ScrollView {
     VStack {

	Image("girlPicture")
	    .border(Color.orange)

	Image("girlPicture")
	    .border(Color.orange, width: 10)

	Image("girlPicture")
	    .opacity(0.5)

	Image("girlPicture")
	    .shadow(radius: 10)

	Image("girlPicture")
	    .shadow(color: .purple, radius: 20, x: 20, y: 20)
    }
}

```

---
## Связаные ссылки:
[[Показать изображение]]
[[Чтобы использовать значок системы]]
[[Добавить стиль к набору системных иконок]]
[[Добавить стиль к изображению]]
[[Image-Web]]
[[Image-Mask]]
[[Image-Blend]]
[[Image-Transform]]
[[Image-Processing]]
[[VStack]]
[[ScrollView]]


---
## Обратные ссылки:
[[01 SwiftUI Helper]]