Tag: #Image #resizable #onAppear #frame #onTapGesture

---
## Описание:
webImage используется для загрузки веб-изображения, используйте URLSession для загрузки исходного изображения после успешной загрузки; вы также можете использовать Kingfisher в функции downloadWebImage.

---
## Скриншот:
![[WebImage.png]]

---
## Код:

``` swift
var body: some View {
        Image(uiImage: self.uiImage ?? placeholderImage)
            .resizable()
            .onAppear(perform: downloadWebImage)
            .frame(width: 80,
                   height: 80,
                   alignment: .center)
            .onTapGesture {
                print("Tap ")
        }
    }

```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[Image]]
