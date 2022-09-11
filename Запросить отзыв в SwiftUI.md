Tag: #StoreKit

---
## Описание:
Метод оценить приложение

---
## Скриншот:


---
## Код:

``` swift
import StoreKit

if let windowScene = UIApplication.shared.windows.first?.windowScene { SKStoreReviewController.requestReview(in: windowScene) }

```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[01 SwiftUI Helper]]