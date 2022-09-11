Tag: #TabView 

---
## Описание:


---
## Скриншот:
![[27TabView.png]]

---
## Код:

``` swift
var body: some View {
	TabView {
	    Text("The home page.")
		.font(.system(size: 36))
		.tabItem({
		    Image(systemName: "house")
		    Text("Home") })
		.tag(0)

	    Text("The settings page")
		.font(.system(size: 36))
		.tabItem({
		    Image(systemName: "gear")
		    Text("Settings")
		})
		.tag(1)
	}
    }
	
```

---
## Связаные ссылки:
[[Text]]
[[Image]]

---
## Обратные ссылки:
[[TabView]]