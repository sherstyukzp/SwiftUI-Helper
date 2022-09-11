Tag: #Image #URLSession #URL #onAppear

---
## Описание:


---
## Скриншот:
![[20Image-Web.png]]

---
## Код:

``` swift
struct ContentView : View {
    
    @State private var remoteImage : UIImage? \= nil
    let placeholderOne = UIImage(named: "Picture")
    
    var body: some View {
        Image(uiImage: self.remoteImage ?? placeholderOne!)
            .onAppear(perform: fetchRemoteImage)
    }
    
    func fetchRemoteImage()
    {
        guard let url \= URL(string: "http://hdjc8.com/images/logo.png") else { return }
        URLSession.shared.dataTask(with: url){ (data, response, error) in
            if let image \= UIImage(data: data!){
                self.remoteImage \= image
            }
            else{
                print(error ?? "")
            }
        }.resume()
    }
}

```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[Image]]