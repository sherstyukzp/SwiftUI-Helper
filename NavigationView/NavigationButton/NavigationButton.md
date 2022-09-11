Tag: #NavigationButton #navigationBarTitle #foregroundColor #font #Text

---
## Описание:
NavigationButtonPage используется для перехода к следующей странице навигации.

---
## Скриншот:
![[NavigationButton.png]]

---
## Код:

``` swift
NavigationLink(destination: NavigationButtonPage()) {
            Text("NavigationButton").bold()
                .foregroundColor(.orange)
                .font(.largeTitle)
            }
    .navigationBarTitle(Text("Page"))
	
```

---
## Связаные ссылки:
[[NavigationLink]]
[[NavigationBarTitle]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]