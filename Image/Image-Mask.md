Tag: #Image #frame #mask #Text #clipShape #Circle #resizable #font

---
## Описание:


---
## Скриншот:
![[18Image-Mask.png]]

---
## Код:

``` swift
VStack{

    Image("girlPicture")
	.clipShape(Circle())

    Image("girlPicture")
	.mask(Circle())

    Image("texture")
    .resizable()
    .frame(width: 300, height: 300)
    .mask(
	Text("SWIFT UI!")
	    .font(Font.system(size: 64).bold()))

}

```

---
## Связаные ссылки:
[[VStack]]
[[Text]]

---
## Обратные ссылки:
[[Image]]