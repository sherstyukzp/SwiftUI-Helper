Tag: #Segment #Picker #VStack #Text #ForEach #pickerStyle #SegmentedPickerStyle

---
## Описание:


---
## Скриншот:
![[25Segment.png]]

---
## Код:

``` swift
struct ContentView : View {
    
    private var animals \= \["🐶 Dog", "🐯 Tiger", "🐷 Pig"\]
    var colors \= \[Color.yellow, Color.orange, Color.red, Color.purple\]
    @State private var selectedAnimal \= 0

    var body: some View {
        VStack {
            Picker(selection: $selectedAnimal, label: Text("animals")) {
               ForEach(0 ..< animals.count) {
                Text(self.animals\[$0\]).tag($0)
               }
            }.pickerStyle(SegmentedPickerStyle())
            Text("Your choice: \\(animals\[selectedAnimal\])")
        }
    }
}

```

---
## Связаные ссылки:
[[VStack]]
[[Picker - обзор]]
[[ForEach]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]
