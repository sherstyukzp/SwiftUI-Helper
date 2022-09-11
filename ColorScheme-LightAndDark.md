Tag: #ColorScheme #VStack #HStack #Text #Image #frame #background #edgesIgnoringSafeArea #environment

---
## Описание:


---
## Скриншот:
![[7ColorScheme-LightAndDark.png]]

---
## Код:

``` swift
struct ContentView : View {
    var body: some View {
        VStack(alignment: .center, spacing: 20){
            Text("Dynamic Type sizes")
                .font(.system(size: 48))
                .foregroundColor(Color.secondary)
            Text("Dynamic Type sizes")
                .foregroundColor(Color.accentColor)
            Image(systemName: "star.fill")
                .foregroundColor(Color.secondary)
                .font(.system(size: 64))
        }
        .frame(minWidth: 0, maxWidth: .infinity, minHeight: 0, maxHeight: .infinity)
        .background(Color.primary)
        .edgesIgnoringSafeArea(.all)
        
    }
}


struct ContentView_Previews : PreviewProvider {
    static var previews: some View {
        HStack {
           ContentView()
              .environment(\.colorScheme, .light)

           ContentView()
              .environment(\.colorScheme, .dark)
        }
        
    }
}


```

---
## Связаные ссылки:
[[VStack]]
[[HStack]]
[[Text]]
[[Image]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]
