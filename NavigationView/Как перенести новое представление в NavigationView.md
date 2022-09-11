Tag: #NavigationView #NavigationLink #Text #navigationBarTitle 

---
## Описание:
Чтобы реализовать поток основных деталей и представить выносной элемент поверх основного вида в NavigationView , используйте

**NavigationLink** \- кнопку, которая запускает навигационную презентацию при нажатии:

---
## Скриншот:
![[Снимок экрана 2021-01-29 в 13.12.18.png]]

---
## Код:

``` swift
struct DetailView: View {
 var body: some View { 

 Text("Detail view")
      } 

}

 struct ContentView: View {
 var body: some View { 

 NavigationView {
 NavigationLink(destination: DetailView()) { 

 Text("Show detail view")
              } 

 .navigationBarTitle("Master view")
          } 

} }
```

NavigationView автоматически обрабатывает добавление кнопки "Назад" при представлении выносного элемента.

---
Если вы хотите добавить заголовок на выносной элемент, используйте модификатор **navigationBarTitle()** внутри тела **DetailView** :

![[Снимок экрана 2021-01-29 в 13.13.45.png]]

``` swift
struct DetailView: View {
 var body: some View { 

 Text("Detail view") 

 .navigationBarTitle("Detail view", displayMode: .inline)
      } 

}
```


---
## Связаные ссылки:
[[NavigationBarTitle]]
[[NavigationLink]]
[[Text]]

---
## Обратные ссылки:
[[NavigationView]]
