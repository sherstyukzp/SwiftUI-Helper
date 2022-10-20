Tag: #TabView #TabBar #ForEach #Image  #Text 

---
## Описание:
> [!INFO]
TabView используется для создания контейнера представления, содержащего нижнюю TabBar

---
## Скриншот:
![[TabView.png]]

---
## Код:

``` swift
TabView(selection: $index) {
    ForEach(0..<imgs.count) { item in
        TabItemPage(index: item)
            .tabItem{
                Image(self.imgs\[item\])
                Text("\\(item)")
        }
        .tag(item)
    }
}

```

---
## Связанные ссылки:
[[Architectural Views]]
[[TabView две вкладки]]
[[ForEach]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]