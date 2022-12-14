Tag: #Text #foregroundColor #bold #font #fontWeight #shadow

---
## Описание:
Текст используется для отображения одной или нескольких строк текстового содержимого с тем же эффектом, что и UILabel, но даже лучше. Если вы хотите создать текст, просто создайте его с помощью текста («SwiftUI»); С помощью синтаксиса с цепочкой вы также можете добавить к тексту несколько атрибутов, таких как шрифты, цвета, тени, интервалы между верхним левым и правым уголками и т. д.

---
## Скриншот:
![[Text.png]]

---
## Код:

``` swift
Text("SwiftUI")
    .foregroundColor(.orange)
    .bold()
    .font(.system(.largeTitle))
    .fontWeight(.medium)
    .italic()
    .shadow(color: .black, radius: 1, x: 0, y: 2)
	
```

---
## Связаные ссылки:
[[Представление, отображающее одну или несколько строк текста только для чтения]]
[[Добавить стиль Text]]
[[Как отформатировать текст внутри текстовых представлений]]
[[Как объединить текстовые представления вместе]]
[[Как задать шрифт и размер Text]]


---
## Обратные ссылки:
[[01 SwiftUI Helper]]

