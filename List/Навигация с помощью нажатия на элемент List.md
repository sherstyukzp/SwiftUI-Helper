Tag: #NavigationLink #List #Text 

---
## Описание:


---
## Скриншот:


---
## Код:

``` swift
let names = ["Thanos", "Iron man", "Ant man"]
List(names) { name in
    NavigationLink(destination: HeroView(name: name)) {
        Text(name)
    }
}
```

---
## Связаные ссылки:
[[NavigationLink]]
[[Text]]

---
## Обратные ссылки:
[[List]]