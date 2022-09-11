Tag: #CLLocation #extension

---
## Описание:
Метод отображение координат в формате градусы, минуты, секунды

---

## Код:

```swift
func getLocationDegreesFrom(latitude: Double) -> String {

    var latSeconds = Int(latitude * 3600)

    let latDegrees = latSeconds / 3600

    latSeconds = abs(latSeconds % 3600)

    let latMinutes = latSeconds / 60

    latSeconds %= 60

    return String(

        format: "%d°%d'%d\"%@",
        abs(latDegrees),
        latMinutes,
        latSeconds,
        latDegrees >= 0 ? "N" : "S"

    )

}

```

```swift
func getLocationDegreesFrom(longitude: Double) -> String {

    var longSeconds = Int(longitude * 3600)

    let longDegrees = longSeconds / 3600

    longSeconds = abs(longSeconds % 3600)

    let longMinutes = longSeconds / 60

    longSeconds %= 60

    return String(

        format: "%d°%d'%d\"%@",
        abs(longDegrees),
        longMinutes,
        longSeconds,
        longDegrees >= 0 ? "E" : "W"

    )

}

```



---
## Связаные ссылки:
[[extension CLLocation вариант 1]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]