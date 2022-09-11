Tag: #NavigationView #Text #navigationBarTitle 

---
## Описание:
NavigationView используется для создания контейнера представления, содержащего верхнюю панель навигации.

---
## Скриншот:
![[NavigationView.png]]

---
## Код:

``` swift
NavigationView {
            Text("🧚‍♂️🧚‍♀️🧜‍♂️🧜‍♀️🧞‍♂️🧞‍♀️").blur(radius: 5)
            Text("Swifter Swifter")
            .bold()
                .foregroundColor(.orange)
                .font(.largeTitle)
        }
    .navigationBarTitle(Text("NavigationView"))
	
```
	
---
## Связаные ссылки:
[[NavigationBarTitle]]
[[Text]]

---
## Обратные ссылки:
[[Architectural Views]]