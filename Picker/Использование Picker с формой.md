Tag: #Picker #Form

---
## Описание:
Picker - это элемент управления в SwiftUI, который позволяет выбрать значение из списка возможных вариантов. Чтобы правильно использовать Picker, необходимо заложить его массивом возможных опций на выбор и переменной состояния, хранящей индекс выбранного параметра в массиве.

В простейшей форме Picker можно использовать следующим образом:

---
## Скриншот:
![[01-SwiftUI-Picker.png]]

---
## Код:

``` swift
struct ContentView: View { 
var frameworks = ["UIKit", "Core Data", "CloudKit", "SwiftUI"] 
@State private var selectedFrameworkIndex = 0 
var body: some View { 
VStack { 
Picker(selection: $selectedFrameworkIndex, label: Text("")) { 
ForEach(0 ..< frameworks.count) { 
Text(self.frameworks[$0]) } } 
Text("Your favorite framework: \(frameworks[selectedFrameworkIndex])") }.padding() 
} 
}

```

---
## Связанные ссылки:
[[Picker - обзор]]
[[Form]]

---
## Обратные ссылки:
[[Picker - обзор]]
