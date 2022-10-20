Tag: #ToolbarItem #Text #NavigationView #toolbar #VStack #Button #Image #navigationBarTrailing

---
## Описание:
> [!INFO] Модель, представляющая элемент, который можно разместить на панели инструментов или панели навигации. Это представляет большинство свойств в UINavigationItem

---
## Скриншот:


---
## Код:
Добавьте `titleView`.

``` swift
NavigationView {    
Text("SwiftUI").padding()        
.toolbar {            
ToolbarItem(placement: .principal) {                
VStack {                    
Text("Title")                    
Button("Clickable Subtitle") 
{ print("principle") }                                    
}            
}        
}        
}

```

Добавьте `leftBarButtonItem` или `leftBarButtonItems`.

```swift
NavigationView {    
Text("SwiftUI").padding()        
.toolbar {            
ToolbarItem(placement: .navigationBarLeading) {                
Button {                                    
} 
label: {                    
Image(systemName: "square.and.pencil")                
}            
}        
}        
}
```

Добавьте `rightBarButtonItem` or `rightBarButtonItems`.

```swift
NavigationView {    
Text("SwiftUI").padding()        
.toolbar {            
ToolbarItem(placement: .primaryAction) {                
Button {                                    
} 
label: {                    
Image(systemName: "square.and.pencil")                
}            
}            
ToolbarItem(placement: .navigationBarTrailing) {                
Button {                                    
} 
label: {                    
Image(systemName: "square.and.pencil")                
}            
}        
}        
}
```

---
## Связаные ссылки:
[[NavigationView]]
[[Button]]
[[Text]]
[[Image]]

---
## Обратные ссылки:
[[01 SwiftUI Helper]]
