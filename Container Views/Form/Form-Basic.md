Tag: #Form #NavigationView #Picker #ForEach #ForEach #Text #pickerStyle #Slider #Toggle #Button #navigationBarTitle

---
## Описание:


---
## Скриншот:
![[13Form-Basic.png]]

---
## Код:

``` swift
struct ContentView : View {

    private var languages \= \["Swift", "Objective-C"\]
    @State private var selectedLanguage \= 0
    @State var workingYear: Double \= 2
    @State var enableNotification \= false

    var body: some View {
        NavigationView {
            Form {
                Picker(selection: $selectedLanguage, label: Text("Languages")) {
                   ForEach(0 ..< languages.count) {
                    Text(self.languages\[$0\]).tag($0)
                   }
                }.pickerStyle(SegmentedPickerStyle())
                HStack{
                    Text("Working years")
                    Slider(value: $workingYear, in: 1...10, step: 1)
                }
                
                Toggle(isOn: $enableNotification) {
                    Text("Enable Notification")
                }

                Button(action: {
                    print("Your programming language: \\(self.languages\[self.selectedLanguage\])")
                    print("Your working years: \\(Int(self.workingYear))")
                    print("Enable notification: \\(self.enableNotification)")
                }) {
                    Text("Submit")
                }
            }.navigationBarTitle(Text("Profiles"))
        }
    }
}

```

---
## Связаные ссылки:
[[Form]]
[[Button]]
[[Toggle]]
[[Text]]
[[HStack]]
[[NavigationBarTitle]]
[[NavigationView]]
[[Slider]]
[[Picker - обзор]]

---
## Обратные ссылки:
[[Form]]