Tag: #List #NavigationView #ForEach #navigationBarItems #onDelete #Text 

---
## Описание:


---
## Скриншот:
![[7List-Delete.png]]

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
                    .onDelete(perform: delete)
                }
                .navigationBarItems(trailing: EditButton())
            }
        }

        func delete(at offsets: IndexSet) {
            if let first \= offsets.first {
                languages.remove(at: first)
            }
        }
    }

```

---
## Связаные ссылки:
[[NavigationView]]
[[NavigationBarItems]]
[[List]]
[[ForEach]]
[[Text]]

---
## Обратные ссылки:
[[List]]