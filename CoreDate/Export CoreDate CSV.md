Tag: #CoreDate #CSV #Button #HStack #Image #Text 

---
## Описание:
Эксопорт CoreDate в формат CSV

---
## Скриншот:


---
## Код:

``` swift

import SwiftUI

struct SettingsView: View {

    @FetchRequest(entity: NPTransaction.entity(), sortDescriptors: []) var transactions: FetchedResults<NPTransaction>
    @State private var isShareSheetShowing = false

    var body: some View {
        NavigationView {
            Button(action: shareButton)
            {
                HStack(alignment: .firstTextBaseline) {
                    Text("Export CSV")
                        .font(.headline)
                    Image(systemName: "square.and.arrow.up")
                        .font(.title)
                }
            }
        }
        .navigationBarTitle("Settings")
    }

    func shareButton() {
        let fileName = "export.csv"
        let path = NSURL(fileURLWithPath: NSTemporaryDirectory()).appendingPathComponent(fileName)
        var csvText = "Date,Type\n"

        for transaction in transactions {
            csvText += "\(transaction.date ?? Date()),\(transaction.type ?? "-")\n"
        }

        do {
            try csvText.write(to: path!, atomically: true, encoding: String.Encoding.utf8)
        } catch {
            print("Failed to create file")
            print("\(error)")
        }
        print(path ?? "not found")

        var filesToShare = [Any]()
        filesToShare.append(path!)

        let av = UIActivityViewController(activityItems: filesToShare, applicationActivities: nil)

        UIApplication.shared.windows.first?.rootViewController?.present(av, animated: true, completion: nil)

        isShareSheetShowing.toggle()
    }

}

struct SettingsView_Previews: PreviewProvider {
    static var previews: some View {
        SettingsView()
    }
}

```

---
## Связаные ссылки:


---
## Обратные ссылки:
[[CoreDate]]