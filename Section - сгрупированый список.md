Tag: #Section 

---
## Описание:
Например, это определяет пример строки и помещает его в сгруппированный список:

---
## Скриншот:


---
## Код:

``` swift
struct ExampleRow: View {
    var body: some View {
        Text("Example Row")
    }
}

struct ContentView: View {
    var body: some View {
        List {
            Section(header: Text("Examples")) {
                ExampleRow()
                ExampleRow()
                ExampleRow()
            }
        }.listStyle(GroupedListStyle())
    }
}


```

---
## Связаные ссылки:
[[List]]
[[Text]]

---
## Обратные ссылки:
[[Section]]