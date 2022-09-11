Tag: #NavigationView #HStack #Button #Image #navigationBarTitle #navigationBarItems

---
## Описание:


---
## Скриншот:
![[10NavigationItem.png]]

---
## Код:

``` swift
struct TrailingButtons : View{
    var body: some View {
        HStack{
            Button(action: {
                print("Download the data")
            }) {
                Image(systemName: "icloud.and.arrow.down.fill")
            }
            Button(action: {
                print("Edit the data")
            }) {
                Image(systemName: "pencil.tip.crop.circle")
            }
        }
    }
}

struct ContentView : View {

    var body: some View {
        NavigationView {
            Text("SwiftUI's NavigationView")
                .navigationBarTitle(Text("SwiftUI"))
                .navigationBarItems(leading:  Button(action: {
                       print("Go to index page")
                   }) {
                       Text("Index")
                   }, trailing: TrailingButtons())
        }
    }
}

```

---
## Связаные ссылки:
[[HStack]]
[[Button]]
[[Text]]
[[NavigationBarTitle]]
[[NavigationBarItems]]

---
## Обратные ссылки:
[[NavigationView]]
