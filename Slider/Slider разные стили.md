Tag: #Slider #VStack #Image #Text #accentColor #systemName

---
## Описание:


---
## Скриншот:
![[23Slider.png]]

---
## Код:

``` swift
struct ContentView : View {
    
     @State var temperature: Double \= 0

       var body: some View {
           VStack {
                Slider(value: $temperature)
                Slider(value: $temperature, in: \-20...40)
                Slider(value: $temperature, in: \-20...40) { (item) in
                    print(item)
                }
                HStack{
                    Image(systemName: "sun.max")

                    Slider(value: $temperature, in: \-20...40, step: 2) { (item) in
                        print(item)
                    }.accentColor(.pink).colorInvert()
                    
                   Image(systemName: "sun.max.fill")
                }.padding()

                Text("The temperature is \\(Int(temperature)).")
           }
       }
}

```

---
## Связаные ссылки:
[[Slider разные стили]]
[[VStack]]
[[HStack]]
[[Image]]

---
## Обратные ссылки:
[[Slider]]
