Tag: #Section 

---
## Описание:
> [!INFO] Например, это определяет пример строки и помещает его в сгруппированный список:

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
## Связанные ссылки:
[[List]]
[[Text]]
[[Section - footer]]
[[Section обзор]]

---
## Обратные ссылки:
[[Section]]
[[01 SwiftUI Helper]]