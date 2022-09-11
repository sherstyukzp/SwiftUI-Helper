Tag: #ScrollView #Image #Text #border #cornerRadius #navigationBarTitle #frame

---
## Описание:
ScrollView - это контейнер для просмотра с прокруткой.

---
## Скриншот:
![[ScrollView.png]]

---
## Код:

``` swift
ScrollView {
    Text("SwiftUI").padding(20)
    Divider()
    Image("icon").resizable()
        .frame(width: 300, height: 300, alignment: .center)
    Divider()
    Text("Views and ... user interface.")
    }
    .border(Color.gray.gradient, width: 1)
            .cornerRadius(10)
            .padding(10)
            .navigationBarTitle(Text("ScrollView"))

```

---
## Связаные ссылки:
[[Text]]
[[Image]]

---
## Обратные ссылки:
[[List]]