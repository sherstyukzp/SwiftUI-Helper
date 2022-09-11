Tag: #Shape #Path #addRoundedRect #addEllipse #addLine

---
## Описание:


---
## Скриншот:
![[32Shape-Path.png]]

---
## Код:

``` swift
Path { path in
   path.move(to: CGPoint(x: 30, y: 0))
   path.addLine(to: CGPoint(x: 30, y: 200))
   path.addLine(to: CGPoint(x: 230, y: 200))
    path.addLine(to: CGPoint(x: 230, y: 0))
}

Path { path in
    path.addEllipse(in: CGRect(x: 100, y: 30, width: 200, height: 200))

    path.addRoundedRect(in: CGRect(x: 100, y: 120, width: 200, height: 200), cornerSize: CGSize(width: 10, height: 10))

    path.addEllipse(in: CGRect(x: 100, y: 210, width: 200, height: 200))
}

```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[Shape]]