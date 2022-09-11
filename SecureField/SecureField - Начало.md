Tag: #SecureField #textFieldStyle

---
## Описание:
Элемент управления, в который пользователь безопасно вводит закрытый текст.

---
## Скриншот:


---
## Код:

``` swift
@State var password: String = "1234"    
var body: some View {
    SecureField($password)
        .textFieldStyle(RoundedBorderTextFieldStyle())
        .padding()
}
```

---


## Связаные ссылки:


---
## Обратные ссылки:
[[SecureField]]