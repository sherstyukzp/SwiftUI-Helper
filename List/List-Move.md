Tag: #List #NavigationView #List #ForEach #Text #onMove #navigationBarTitle #navigationBarItems

---
## Описание:


---
## Скриншот:
![[8List-Move.png]]

---
## Код:

``` swift
struct ContentView : View {
    @State var languages \= \["Objective-C", "Swift", "Flutter"\]

    var body: some View {
        NavigationView {
            List {
                ForEach(languages,id: \\.self) { language in
                    Text(language)
                }
                .onMove { (source, destination) in
                    self.languages.move(fromOffsets: source, toOffset: destination)
                }
            }
            .navigationBarTitle(Text("Edit Row"), displayMode: .large)
            .navigationBarItems(trailing: EditButton())
        }
    }

    func moveItem(from source: IndexSet, to destination: Int) {
        languages.move(fromOffsets: source, toOffset: destination)
        print(languages)
    }
}

```

---
## Связаные ссылки:
[[NavigationView]]
[[ForEach]]
[[Text]]
[[NavigationBarTitle]]
[[NavigationBarItems]]

---
## Обратные ссылки:
[[List]]