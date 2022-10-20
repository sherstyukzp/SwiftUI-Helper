Teg: #WebView #URLRequest #URL #UIViewRepresentable

---
## Описание:
> [!INFO] WebView используется для отображения открытой веб-страницы, например:

---
## Скриншот:
![[WebView.png]]

---
## Код:

``` swift
struct WebViewPage : UIViewRepresentable {
    func makeUIView(context: Context) \-> WKWebView  {
        return WKWebView()
    }
    func updateUIView(\_ uiView: WKWebView, context: Context) {
        let req \= URLRequest(url: URL(string: "https://www.apple.com")!)
        uiView.load(req)
    }
}
```

---
## Связаные ссылки:

---
## Обратные ссылки:
[[01 SwiftUI Helper]]