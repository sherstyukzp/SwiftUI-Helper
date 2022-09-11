Tag: #CLLocation #extension

---
## Описание:
Метод отображение координат в формате градусы, минуты, секунды

---

## Код:

```swift
extension BinaryFloatingPoint {
    var dms: (degrees: Int, minutes: Int, seconds: Int) {
        var seconds = Int(self * 3600)
        let degrees = seconds / 3600
        seconds = abs(seconds % 3600)
        return (degrees, seconds / 60, seconds % 60)
    }
}

```

```swift
extension CLLocation {
    var dms: String { latitude + " " + longitude }
    var latitude: String {
        let (degrees, minutes, seconds) = coordinate.latitude.dms
        return String(format: "%d°%d'%d\"%@", abs(degrees), minutes, seconds, degrees >= 0 ? "N" : "S")
    }
    var longitude: String {
        let (degrees, minutes, seconds) = coordinate.longitude.dms
        return String(format: "%d°%d'%d\"%@", abs(degrees), minutes, seconds, degrees >= 0 ? "E" : "W")
    }
}

```

```swift
let latitude = -22.9133950
let longitude = -43.2007100
let location = CLLocation(latitude: latitude, longitude: longitude)
location.latitude  // "22°54'48"S"
location.longitude // "43°12'2"W"
location.dms       // "22°54'48"S 43°12'2"W"

```

---
## Связаные ссылки:
[[extension CLLocation вариант 2]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]