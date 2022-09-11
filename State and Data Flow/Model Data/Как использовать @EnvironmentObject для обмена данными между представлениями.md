Tag: #ObservableObject #NavigationLink #NavigationView #Button #Text #Published

---
## Описание:
> [!Info] 
> Код показывает как передавать данные из одного представления в другое.
> Код проверил, супер

---
## Скриншот:


---
## Код:

``` swift
class UserSettings: ObservableObject {

private init() { }

static let shared = UserSettings()

@Published var score = 0

}

struct ContentView: View {

@ObservedObject var settings: UserSettings = .shared

var body: some View {

NavigationView {

VStack {

// A button that writes to the environment settings

Button(action: {

self.settings.score += 1

}) {

Text("Increase Score")

}

NavigationLink(destination: DetailView()) {

Text("Show Detail View")

}

}

}

}

}

struct DetailView: View {

@ObservedObject var settings: UserSettings = .shared

var body: some View {

// A text view that reads from the environment settings

Text("Score: \(settings.score)")

}
}

```

---
## Связанные ссылки:
[[NavigationLink]]
[[Text]]
[[Button]]

---
## Обратные ссылки:
[[NavigationView]]
