Tag: #Gesture #VStack #onChanged #Circle #frame #animation

---
## Описание:


---
## Скриншот:
![[5DragGesture.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
    @State var offset: CGSize \= .zero
    
    var body: some View {
        let dragGesture \= DragGesture()
            .onChanged { (value) in
                print(value.startLocation, value.location, value.translation)
                self.offset \= value.translation
            }
            .onEnded { (value) in
                if(abs(value.translation.width) \>= 40 || abs(value.translation.height \- (\-260)) \>= 40){
                    self.offset \= .zero
                }
                else{
                    self.offset \= CGSize(width: 0, height: \-260)
                }
            }
        
        return VStack{
            Circle()
                .fill(Color.black)
                .opacity(0.1)
                .frame(width: 200, height: 200)
                .offset(CGSize(width: 0, height: \-50))
            
            Circle()
                .fill(Color.orange)
                .frame(width: 200, height: 200)
                .offset(offset)
                .gesture(dragGesture)
                .animation(.spring())
        }
        
    }
}

```

---
## Связаные ссылки:
[[VStack]]

---
## Обратные ссылки:
[[Gesture]]