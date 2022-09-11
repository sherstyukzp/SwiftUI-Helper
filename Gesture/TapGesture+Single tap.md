Tag: #Gesture #TapGesture #Circle #frame #fill #scaleEffect #animation

---
## Описание:


---
## Скриншот:
![[1TapGesture+Singletap.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
    @State var isPressed \= false
    
    var body: some View {
        let tapGesture \= TapGesture()
            .onEnded { \_ in
                self.isPressed.toggle()
        }
        
        return Circle()
            .fill(Color.orange)
            .frame(width: 240, height: 240)
            .gesture(tapGesture)
            .scaleEffect(isPressed ? 1.4 : 1)
            .animation(.default)
    }
}

```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[Gesture]]

