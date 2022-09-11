



Tag: #TextField #textFieldStyle #SecureField

--- 
## Описание:


---
## Скриншот:
![[2 1.png]]

---
## Код:

``` swift
@State var password: String = "" // create State

SecureField($password) // passing it to bind
    .textFieldStyle(.roundedBorder) // adds border
```

---


## Связаные ссылки:
[[SecureField]]

---
## Обратные ссылки:
[[TextField]]