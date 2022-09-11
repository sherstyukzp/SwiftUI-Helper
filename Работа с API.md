Tag: #API

---
## Описание:


---
## Скриншот:
![[Simulator Screen Shot - iPhone 11 - 2021-04-14 at 11.19.57.png]]

---
## Код:
ContentView
``` swift
//
//  ContentView.swift
//  ARITask
//
//  Created by Ярослав Шерстюк on 13.04.2021.
//

import SwiftUI

struct ContentView: View {
    
    @State var results = [Podcast]()
    
    var body: some View {
        
        NavigationView {
            
            List(results, id: \.id) { item in
                
                NavigationLink(destination: DetailView(itemSelect: item)) {
                    VStack(alignment: .leading) {
                        HStack {
                            ZStack {
                                
                                RemoteImage(url: item.images.default!.absoluteString)
                                    .aspectRatio(contentMode: .fit)
                                    .frame(width: 100, height: 100, alignment: .center)
                                    .cornerRadius(10)
                                    .overlay(RoundedRectangle(cornerRadius: 10)
                                                .stroke(Color.secondary, lineWidth: 2))
                                    .shadow(radius: 10)
                                    .padding([.top, .bottom, .trailing])
                                
                                if item.isExclusive {
                                    Image ("ic_exclusive")
                                        .resizable()
                                        .frame(width: 100, height: 100, alignment: .center)
                                        .cornerRadius(10)
                                        .overlay(RoundedRectangle(cornerRadius: 10)
                                                    .stroke(Color.secondary, lineWidth: 2))
                                        .padding([.top, .bottom, .trailing])
                                    
                                }
                            }
                            
                            VStack (alignment: .leading){
                                Text(item.title)
                                    .font(.largeTitle)
                                    .multilineTextAlignment(.leading)
                                    .lineLimit(1)
                                HStack {
                                    Text(item.publisherName)
                                    Spacer()
                                    if item.hasFreeEpisodes {
                                        Text("FREE")
                                            .foregroundColor(.white)
                                            .background(Color(.red))
                                            .font(.callout)
                                            
                                        
                                    }
                                }
                                
                                Divider()
                                Text(item.categoryName).foregroundColor(.orange)
                            }
                        }
                    }
                }
                
            }
            .onAppear(perform: loadData)
        
            .navigationTitle(Text ("Podcast"))
            
        }
        
    }
    
    
    func loadData() {
        guard let url = URL(string: "https://601f1754b5a0e9001706a292.mockapi.io/podcasts") else {
            print("Invalid URL")
            return
        }
        let request = URLRequest(url: url)
        
        URLSession.shared.dataTask(with: request) { data, response, error in
            if let data = data {
                if let response = try? JSONDecoder().decode([Podcast].self, from: data) {
                    DispatchQueue.main.async {
                        self.results = response
                    }
                    return
                }
            }
        }.resume()
    }
    
    
}


struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

```

RemoteImage
``` swift
//
//  RemoteImage.swift
//  ARITask
//
//  Created by Ярослав Шерстюк on 13.04.2021.
//

import SwiftUI

struct RemoteImage: View {
    private enum LoadState {
        case loading, success, failure
    }

    private class Loader: ObservableObject {
        var data = Data()
        var state = LoadState.loading

        init(url: String) {
            guard let parsedURL = URL(string: url) else {
                fatalError("Invalid URL: \(url)")
            }

            URLSession.shared.dataTask(with: parsedURL) { data, response, error in
                if let data = data, data.count > 0 {
                    self.data = data
                    self.state = .success
                } else {
                    self.state = .failure
                }

                DispatchQueue.main.async {
                    self.objectWillChange.send()
                }
            }.resume()
        }
    }

    @StateObject private var loader: Loader
    var loading: Image
    var failure: Image

    var body: some View {
        selectImage()
            .resizable()
    }

    init(url: String, loading: Image = Image(systemName: "photo"),
         failure: Image = Image(systemName: "photo")) {
        _loader = StateObject(wrappedValue: Loader(url: url))
        self.loading = loading
        self.failure = failure
    }

    private func selectImage() -> Image {
        switch loader.state {
        case .loading:
            return loading
        case .failure:
            return failure
        default:
            if let image = UIImage(data: loader.data) {
                return Image(uiImage: image)
            } else {
                return failure
            }
        }
    }
}

```      

Podcast
``` swift
import Foundation

struct Images: Codable {
    let `default`: URL?
    let featured: URL?
    let thumbnail: URL?
    let wide: URL?
}

struct Podcast: Codable {
    let id: String
    let title: String
    let images: Images
    let isExclusive: Bool
    let publisherName: String
    let publisherId: String
    let mediaType: String
    let description: String
    let categoryId: String
    let categoryName: String
    let hasFreeEpisodes: Bool
    let playSequence: String
}

```   

DetailView
``` swift
import SwiftUI

struct DetailView: View {
    
    let itemSelect: Podcast
    
    var body: some View {
        
        VStack {
            RemoteImage(url: itemSelect.images.default!.absoluteString)
                .aspectRatio(contentMode: .fit)
                .frame(width: 300, height: 300, alignment: .center)
                .cornerRadius(10)
                .overlay(RoundedRectangle(cornerRadius: 10)
                            .stroke(Color.secondary, lineWidth: 2))
                .shadow(radius: 10)
            Text("\(itemSelect.publisherName)").font(.title)
            Text("\(itemSelect.playSequence)")
            Divider()
            HStack(alignment: .center) {
                Text("Description")
                    .font(.title)
                    .fontWeight(.bold)
                    .padding(.leading)
                Spacer()
                
            }
            
                
            Text("\(itemSelect.description)")
                .padding()
                .foregroundColor(.gray)

            Spacer ()
        }
            
            
            .navigationTitle(Text("\(itemSelect.title)"))
        
        
        
    }
}

```


---
## Связаные ссылки:


---
## Обратные ссылки:
[[01 SwiftUI Helper]]