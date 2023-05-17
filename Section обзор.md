Tag: #Section 

---
## Описание:


---
## Скриншот:


---
## Код:

``` swift
struct ContentView: View {
    var body: some View {
        List {
            Section(header: Text("Important tasks")) {
                TaskRow()
                TaskRow()
                TaskRow()
            }

            Section(header: Text("Other tasks")) {
                TaskRow()
                TaskRow()
                TaskRow()
            }
        }
    }
}

```

---
## Связанные ссылки:
[[List]]
[[Section - footer]]
[[Section - сгрупированый список]]

---
## Обратные ссылки:
[[Section]]
[[01 SwiftUI Helper]]