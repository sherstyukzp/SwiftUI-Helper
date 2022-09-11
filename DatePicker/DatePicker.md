Tag: #DatePicker #Text #VStack 

---
## Описание:
DatePicker используется для выбора абсолютной даты элемента управления.

---
## Скриншот:
![[22PickerDate.png]]

---
## Код:

``` swift
struct ContentView : View {
    var myDateFormatter: DateFormatter {
        let formatter = DateFormatter()
        formatter.dateStyle = .long
        return formatter
    }

    @State var selectedDate = Date()

    var body: some View {
        VStack {
            DatePicker(selection: $selectedDate, displayedComponents: DatePickerComponents.hourAndMinute) {
                Text("Date")
            }
            
            DatePicker(selection: $selectedDate, displayedComponents: DatePickerComponents.date) {
                Text("Date")
            }

            DatePicker(selection: $selectedDate,in: Date()...Date().advanced(by: 7*24*3600), displayedComponents: [.date, .hourAndMinute]) {
                Text("Date")
            }

            Text("Your Choice: \(selectedDate, formatter: myDateFormatter)")
        }
    }
}
				
```



---
## Связаные ссылки:
[[DatePicker]]
[[Как локализировать DatePicker]]
[[VStack]]
[[Text]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]