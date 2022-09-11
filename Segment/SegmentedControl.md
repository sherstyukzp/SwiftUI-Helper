Tag: #SegmentedControl #ForEach #Text #tapAction

---
## Описание:
SegmentedControl используется для выбора условия сегментации, например:

---
## Скриншот:
![[SegmentedControl.png]]

---
## Код:

``` swift
SegmentedControl(selection: $currentIndex) {
    ForEach(0..<items.count) { index in
        Text(self.items\[index\]).tag(index)
    }
    }.tapAction {
        print("currentIndex: \\(self.currentIndex)")
}

```

---
## Связаные ссылки:
[[ForEach]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]