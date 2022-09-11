Tag: #NavigationView 

---
## Описание:
По умолчанию в заголовке панели навигации используется режим отображения **.large** , который представлен на скриншоте выше.

Измените режим отображения заголовка на панели навигации на **.inline** , чтобы сделать заголовок маленьким:

---
## Скриншот:
![[Снимок экрана 2021-01-29 в 12.56.13.png]]

---
## Код:

``` swift
NavigationView {
 Text("SwiftUI tutorials")
       .navigationBarTitle("Master view", displayMode: .inline) 

}
```

---
## Связаные ссылки:
[[NavigationBarTitle]]
[[Text]]

---
## Обратные ссылки:
[[NavigationView]]