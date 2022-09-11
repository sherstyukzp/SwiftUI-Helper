Tag: #ForEach #Text #bold #font

---
## Описание:
ForEach используется для представления на основе набора существующих данных.

---
## Скриншот:
![[ForEach.png]]

---
## Код:

``` swift
let data = (0..<5)
var body: some View {
    ForEach(data) { e in
        Text("Hello \(e)")
            .bold()
            .font(.system(size: 25, design: .monospaced))
            .padding(5)
}

```

---
## Связаные ссылки:
[[ForEach]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]