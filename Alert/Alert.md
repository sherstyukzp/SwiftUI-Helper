Tag: #Alert 

---
## Описание:


---
## Скриншот:
![[AlertPage.jpg]]

---
## Код:

``` swift
alert(isPresented: $showAlert, content: {
            Alert(title: Text("确定要支付这100000000美元吗？"),
                  message: Text("请谨慎操作\\n一旦确认，钱款将立即转入对方账户"),
                  primaryButton: .destructive(Text("确认")) { print("转出中...") },
                  secondaryButton: .cancel())
        }).navigationBarTitle(Text("Alert"))
		
```

---


## Связаные ссылки:


---
## Обратные ссылки:
[[01 SwiftUI Helper]]