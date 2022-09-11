Tag: #List #NavigationView #ForEach #onDelete #onMove #navigationBarTitle #navigationBarItems

---
## Описание:


---
## Скриншот:
![[9List-DeleteAndMove.png]]

---
## Код:

``` swift
struct ContentView : View {
    @State var languages \= \["Objective-C", "Swift", "Flutter"\]

    var body: some View {
        NavigationView {
            List {
                ForEach(languages, id: \\.self) { language in
                    Text(language)
                }
                .onDelete(perform: deleteItem)
                .onMove(perform: moveItem)
            }
            .navigationBarTitle(Text("Edit Row"), displayMode: .large)
            .navigationBarItems(trailing: EditButton())
        }
    }

    func deleteItem(at offsets: IndexSet) {
        if let first \= offsets.first {
            languages.remove(at: first)
        }
    }
    
    func moveItem(from source: IndexSet, to destination: Int) {
        languages.move(fromOffsets: source, toOffset: destination)
    }
}

```

---
## Связаные ссылки:
[[NavigationView]]
[[NavigationBarTitle]]
[[NavigationBarItems]]
[[ForEach]]

---
## Обратные ссылки:
[[List]]