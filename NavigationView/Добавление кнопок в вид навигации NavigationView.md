Tag: #NavigationView #navigationBarTitle #navigationBarItems 

---
## Описание:
Добавьте начальные и конечные кнопки на панель навигации с помощью модификатора навигационной панели . Начальный кнопка \- это символ SF, замыкающая кнопка \- это текст:

---
## Скриншот:
![[Снимок экрана 2021-01-29 в 12.58.58.png]]

---
## Код:

``` swift
NavigationView {
 Text("SwiftUI tutorials")
       .navigationBarTitle("Master view")
       .navigationBarItems(leading: 

 Button(action: {
 print("SF Symbol button pressed...") 

 }) { Image(systemName: "calendar.circle").imageScale(.large) 

}, trailing:

 Button(action: {
 print("Edit button pressed...") 

 }) { Text("Edit") 

} )

}

```

Вы можете добавить несколько кнопок к элементам начальющей или задней панели с помощью HStack :

![[Снимок экрана 2021-01-29 в 13.10.23.png]]

``` swift
NavigationView {
 Text("SwiftUI tutorials")
      .navigationBarTitle("Master view")
      .navigationBarItems(trailing: 

 HStack {
 Button(action: { 

 print("SF Symbol button pressed...")
              }) { 

 Image(systemName: "calendar.circle")
                      .imageScale(.large) 

 } Button(action: { 

 print("Edit button pressed...")
              }) { 

 Text("Edit")
              } 

} )

}

```



---
## Связаные ссылки:
[[NavigationBarItems]]
[[NavigationBarTitle]]

---
## Обратные ссылки:
[[NavigationView]]