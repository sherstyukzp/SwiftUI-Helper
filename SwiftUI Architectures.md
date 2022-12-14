## Model-View

![[ModelView.jpeg]]

Архитектура Model-View не обеспечивает абстрагирование бизнес-логики из представлений, аналогичного шаблону архитектуры MVC с UIKit.

---

## Redux

![[Redux.jpeg]]

В архитектурах подобных Redux, глобальное состояние используется для обеспечения согласованности всех представлений, хранящихся в магазинах. Компоненты просмотра могут инициировать действия, которые интерпретируются редуктором в изменения состояния.

---

## MVVM ViewState

![[MVVM.jpeg]]

ViewState MVVM использует отдельные ViewModels для каждого вида (при необходимости). Вместо глобального состояния и глобальных действий ViewState MVVM создает отдельный интерфейс ViewModel для каждого представления, содержащего состояние и различные входы.

---
## Обратные ссылки:
[[01 SwiftUI Helper]]