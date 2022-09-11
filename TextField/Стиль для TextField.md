Tag: #TextField #padding #background #cornerRadius

---
## Описание:
**Шаг 1:** Создайте свойство State, которое содержит входные данные пользователя. Для получения дополнительной информации о том, как работают свойства состояния и как они используются с текстовыми полями, ознакомьтесь с нашим [руководством по странице входа](https://www.blckbirds.com/post/login-page-in-swiftui-1)!

**Шаг 2:** Инициализация объекта TextField. Введите строку, которая служит заполнителем, когда TextField пуст. Затем вам нужно привязать созданное состояние с TextField, чтобы включить поток данных между ними. Чтобы понять концепцию потока данных в SwiftUI, мы также рекомендуем вам наше [руководство по странице входа](https://blckbirds.com/post/login-page-in-swiftui-1/) в [систему](https://blckbirds.com/post/login-page-in-swiftui-1/).  

**Шаг 3:** В SwiftUI мы стилизуем текстовое поле, добавляя к нему модификаторы. Например, вы можете добавить скругленный фон и дополнения в TextField

---
## Скриншот:
![[Снимок экрана 2021-01-30 в 20.33.01.png]]

---
## Код:

``` swift
import SwiftUI

let lightGreyColor = Color(red: 239.0/255.0, green: 243.0/255.0, blue: 244.0/255.0, opacity: 1.0)

struct ContentView : View {
    //Create a State property that holds the user's input
    @State var userInput = ""

    var body: some View {
        //Initialize the Text Field, provide it with a placeholder title and bind it to the State
        TextField("Enter something...", text: $userInput)
            //Style your Text Field
            .padding()
            .background(lightGreyColor)
            .cornerRadius(5.0)
            .padding()
    }
}
```


---
## Связаные ссылки:


---
## Обратные ссылки:
[[TextField]]