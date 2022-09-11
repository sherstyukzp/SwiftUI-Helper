Tag: #Playground #VStack #Text #Button

---
## Описание:
Пример работы с Playground. Код также подходит для работы на iPad

---
## Скриншот:
![[image1.png]]

---
## Код:

``` swift
import PlaygroundSupport

import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Text("Hello!")
            Button(action: {
                print("Clicked")
            }, label: { Text("Click Me!") })
        }
    }
}


PlaygroundPage.current.setLiveView(ContentView())

```

---
## Связаные ссылки:
[[VStack]]
[[Text]]
[[Button]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]