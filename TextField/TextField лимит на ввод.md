Tag: #TextField 

---
## Описание:
Два способа как сделать лемит на воод в поле TextField

---
## Скриншот:


---
## Код:
Способ 1 использую  `Binding` extension

``` swift
extension Binding where Value == String {
    func max(_ limit: Int) -> Self {
        if self.wrappedValue.count > limit {
            DispatchQueue.main.async {
                self.wrappedValue = String(self.wrappedValue.dropLast())
            }
        }
        return self
    }
}



struct DemoView: View {
    @State private var textField = ""
    var body: some View {
        TextField("8 Char Limit", text: self.$textField.max(8)) // Here
            .padding()
    }
}

```

Способ 2 использую `onChange(of:perform:)`

``` swift
struct ContentView: View {
  @State private var text: String = ""

  var body: some View {
    VStack {
      TextField("Name", text: $text, prompt: Text("Name"))
        .onChange(of: text, perform: {
          text = String($0.prefix(1))
        })
    }
  }
}

struct ContentView_Previews: PreviewProvider {
  static var previews: some View {
    ContentView()
      .previewDevice(.init(rawValue: "iPhone SE (1st generation)"))
  }
}

```

Второй способ наиболее подходящий

---
## Связаные ссылки:
[[TextField]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]