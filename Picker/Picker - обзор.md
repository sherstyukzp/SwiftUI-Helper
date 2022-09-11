Tag: #Picker #Text  #Frame #ForEach #UIScreen

---
## Описание:


---
## Скриншот:
![[Picker.png]]

---
## Код:

``` swift
Picker(selection: $leftIndex, label: Text("Picker")) {
    ForEach(0..<leftSource.count) {
        Text(self.leftSource\[$0\]).tag($0)
    }
    }.frame(width: UIScreen.main.bounds.width/2)
	
```

---
## Связаные ссылки:
[[ForEach]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]