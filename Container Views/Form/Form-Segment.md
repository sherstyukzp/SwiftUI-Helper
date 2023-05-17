Tag: #Form #NavigationView #Form #Section #Text #ForEach #HStack #Slider #Toggle

---
## Описание:


---
## Скриншот:
![[14Form-Segment.png]]

---
## Код:

``` swift
struct ContentView : View {
    private var languages = ["Swift", "Objective-C"]
    @State private var selectedLanguage = 0
    @State var workingYear: Double = 2
    @State var enableNotification = false
    var body: some View {
        NavigationView {
            Form {
                Section(header: Text("Please enter your information:"), footer: Text("Note: Enabling notification to get more infomration")) {
                    Picker(selection: $selectedLanguage, label: Text("Languages")) {
                       ForEach(0 ..< languages.count) {
                        Text(self.languages[$0]).tag($0)
                       }
                    }.pickerStyle(SegmentedPickerStyle())
                    HStack{
                        Text("Working years")
                        Slider(value: $workingYear, in: 1...10, step: 1)
                    }
                    
                    Toggle(isOn: $enableNotification) {
                        Text("Enable Notification")
                    }
                }
                Button(action: {
                // activate theme!
                    print("Your programming language: \(self.languages[self.selectedLanguage])")
                    print("Your working years: \(Int(self.workingYear))")
                    print("Enable notification: \(self.enableNotification)")
                }) {
                    Text("Submit")
                }
            }.navigationBarTitle(Text("Profiles"))
        }
    }
}

```

---
## Связанные ссылки:
[[NavigationView]]
[[NavigationBarTitle]]
[[Container Views/Section]]
[[Picker - обзор]]
[[Form]]
[[ForEach]]
[[Toggle]]
[[Button]]
[[Text]]
[[HStack]]

---
## Обратные ссылки:
[[Form]]