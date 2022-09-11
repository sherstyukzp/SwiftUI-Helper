Tag: #MapView #MapKit #makeUIView #updateUIView #MKMapView #MKCoordinateRegion #MKCoordinateSpan #CLLocationCoordinate2D #func #showsUserLocation #mapType

---
## Описание:


---
## Скриншот:
![[29MapView.png]]

---
## Код:

``` swift
import SwiftUI
import MapKit

struct ContentView : UIViewRepresentable {
    
    func makeUIView(context: UIViewRepresentableContext<ContentView>) -> MKMapView {
        return MKMapView()
    }
    
    func updateUIView(_ uiView: MKMapView, context: UIViewRepresentableContext<ContentView>) {
        uiView.showsUserLocation \= true
        uiView.mapType = MKMapType.satellite
        
        let coordinate2D = CLLocationCoordinate2D(latitude: 39.915352, longitude: 116.397105)
        let zoomLevel \= 0.02
        let region = MKCoordinateRegion(center: coordinate2D, span: MKCoordinateSpan(latitudeDelta: zoomLevel, longitudeDelta: zoomLevel))
        uiView.setRegion(uiView.regionThatFits(region), animated: true)
    }
}

```

---
## Связаные ссылки:
[[Как сделать создание новой метки на карте]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]