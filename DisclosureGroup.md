Tag: #DisclosureGroup

---
## Описание:
Представление группы раскрытия состоит из метки для идентификации содержимого и элемента управления для отображения и скрытия содержимого. Показ содержимого приводит группу раскрытия в «расширенное» состояние, а их скрытие приводит к «спаду» группы раскрытия информации.

---
## Скриншот:


---
## Код:

``` swift
struct ToggleStates { 
var oneIsOn: Bool = false 
var twoIsOn: Bool = true
}

@State private var toggleStates = ToggleStates()
@State private var topExpanded: Bool = true 
var body: some View { 
DisclosureGroup("Items", isExpanded: $topExpanded) { 
Toggle("Toggle 1", isOn: $toggleStates.oneIsOn) 
Toggle("Toggle 2", isOn: $toggleStates.twoIsOn) 
DisclosureGroup("Sub-items") { 
Text("Sub-item 1") } 
}
}

```

---
## Связанные ссылки:


---
## Обратные ссылки:
[[01 SwiftUI Helper]]