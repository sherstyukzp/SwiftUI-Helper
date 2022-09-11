Tag: #Gesture #frame #scaleEffect #animation #onTapGesture #Circle #fill #animation

---
## Описание:


---
## Скриншот:
![[2TapGesture+Doubletap.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
    @State var isPressed = false
    
    var body: some View {
        
        return Circle()
            .fill(Color.orange)
            .frame(width: 240, height: 240)
            .scaleEffect(isPressed ? 1.4 : 1)
            .animation(.default)
            .onTapGesture(count: 2) {
                self.isPressed.toggle()
                print("Double tap.")
        }
    }
}

```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[Gesture]]