Tag: #Image #ZStack #VStack #blendMode

---
## Описание:


---
## Скриншот:
![[17Image-Blend.png]]

---
## Код:

``` swift
VStack {
            
    Image("girlPicture")
	.blendMode(.difference)

    ZStack{
	Image("texture")
	Image("girlPicture")
	    .blendMode(.multiply)
    }
}
.padding()

```

---
## Связаные ссылки:
[[VStack]]
[[ZStack]]

---
## Обратные ссылки:
[[Image]]