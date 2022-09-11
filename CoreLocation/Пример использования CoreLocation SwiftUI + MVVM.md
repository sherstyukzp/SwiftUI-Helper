Tag: #CoreLocation #NSObject #ObservableObject #CLLocation

---
## Описание:


---
## Скриншот:


---
## Код:

```Swift

import Foundation
import Combine
import CoreLocation

class LocationViewModel: NSObject, ObservableObject{
  
  @Published var userLatitude: Double = 0
  @Published var userLongitude: Double = 0
  
  private let locationManager = CLLocationManager()
  
  override init() {
    super.init()
    self.locationManager.delegate = self
    self.locationManager.desiredAccuracy = kCLLocationAccuracyBest
    self.locationManager.requestWhenInUseAuthorization()
    self.locationManager.startUpdatingLocation()
  }
}

extension LocationViewModel: CLLocationManagerDelegate {
  
  func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
    guard let location = locations.last else { return }
    userLatitude = location.coordinate.latitude
    userLongitude = location.coordinate.longitude
    print(location)
  }
}

```

Теперь пришло время использовать его в представлении.

```Swift

struct LocationView: View {
  
  @ObservedObject var locationViewModel = LocationViewModel()
  
  var body: some View {
    VStack {
      Text("Your location is:")
      HStack {
        Text("Latitude: \(locationViewModel.userLatitude)")
        Text("Longitude: \(locationViewModel.userLongitude)")
      }
    }
  }
}

```

> [!Warning] Последний шаг - добавить ключ NSLocationWhenInUseUsageDescription с описанием в файл Info.plist, чтобы ваше приложение получило разрешение на использование местоположения пользователя:

![[ask_location_permission.png]]

---

## Связаные ссылки:

[[MapView]]


---
## Обратные ссылки:
[[01 SwiftUI Helper]]
