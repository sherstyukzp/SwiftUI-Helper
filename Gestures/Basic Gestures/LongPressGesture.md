Tag: #Gesture #Circle #updating #onEnded #frame #fill #animation #scaleEffect

---
## Описание:


---
## Скриншот:
![[3LongPressGesture.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
    @GestureState var isLongPressed \= false
    
    var body: some View {
        let longPressGesture \= LongPressGesture()
            .updating($isLongPressed) { value, state, transcation in
                print(value, state, transcation)
                state \= value
            }
            .onEnded { (value) in
                print(value)
            }
        
        return Circle()
            .fill(Color.orange)
            .frame(width: 240, height: 240)
            .gesture(longPressGesture)
            .scaleEffect(isLongPressed ? 1.4 : 1)
            .animation(.default)
    }
}

```


---
## Связаные ссылки:


---
## Обратные ссылки:
[[Basic Gestures]]