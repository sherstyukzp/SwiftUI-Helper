Tag: #Gesture #onChanged #onEnded #rotationEffect #RotationGesture

---
## Описание:


---
## Скриншот:
![[4RotationGesture.gif]]

---
## Код:

``` swift
struct ContentView : View {
    
    @State var angle \= 0.0
    
    var body: some View {
        let rotationGesture \= RotationGesture(minimumAngleDelta: Angle.init(degrees: 20))
            .onChanged({ (angle) in
                
                self.angle += angle.animatableData
            }).onEnded { (angle) in
                print(self.angle)
        }
        
        return Image("logo")
            .gesture(rotationGesture)
            .rotationEffect(Angle.init(degrees: self.angle))
    }
}

```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[Gesture]]