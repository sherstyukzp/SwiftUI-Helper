SwiftUI богат обертками для работы с данными. Подробней ознакомиться с тем, что такое Property Wrapper’ы (обертки) и с чем их едят, можно в моей предыдущей статье [Property Wrappers в Swift](https://blog.noveogroup.ru/2020/11/property-wrappers-v-swift/). А в этом посте мы рассмотрим практическое применение существующих оберток для работы с данными в SwiftUI.

Основной момент: если меняется значение внутри переменной любой из указанных оберток, и эта переменная используется внутри переменной body, — переменная body будет вычислена повторно, таким образом View обновится (перерисуется).

Итак, первой оберткой является State.

## @State

Исходя из документации Apple, [State](https://developer.apple.com/documentation/swiftui/state) необходимо использовать для хранения данных конкретной View. [Здесь](https://developer.apple.com/documentation/swiftui/state-and-data-flow) Apple советует в @State хранить именно UI-состояние, а не бизнес-логику: «_Manage transient UI state locally within a view by wrapping value types as State properties_.»

Более того, очень важно работать с этой переменной только внутри View, где она была объявлена, причем только из переменной body или из методов, которые вызываются из переменной body. Поэтому всегда стоит объявлять @State приватной переменной.

«_You should only access a state property from inside the view’s body, or from methods called by it. For this reason, declare your state properties as private, to prevent clients of your view from accessing them. It is safe to mutate state properties from any thread_.»

Приведу простой пример использования @State, он искусственный (как раз View-счетчик обычно полезно инициализировать значениями извне), но с ним проще играться.

``` Swift
import SwiftUI

struct SimplestState: View {
    @State private var counter = 0
    var body: some View {
        VStack(alignment: .center, spacing: 20) {
            Text("counter: \(counter)")
                .font(.title)
            HStack(spacing: 20) {
                Button("Increase") {
                    counter += 1
                }

                Button("Decrease") {
                    counter = max(0, counter - 1)
                }
                .disabled(counter == 0)
            }
        }
    }
}

struct SimplestState_Previews: PreviewProvider {
    static var previews: some View {
        SimplestState()
    }
}
```

Хотел бы обратить внимание еще на одну вещь. Хранить в @State стоит только простые типы (Int, String, Bool), ну или в крайнем случае — структуры, но ни в коем случае не классы. Почему? Ну просто потому, что с классами State не будет работать.

Об этом косвенно упоминается в документации фразой «_When the state value changes, the view invalidates its appearance and recomputes the body_.» Подозреваю, что если бы был протокол, который ограничивает, что его может реализовать только структура, но не класс, — данная обертка использовала бы его (по аналогии с AnyObject для классов).

Если мы используем @State для структуры, то любое изменение любого ее поля по факту «под капотом» приведет к созданию новой копии структуры, которая перепишет значение переменной в State, что вызовет перерисовку View.

В случае же класса этого не произойдет. Но не стоит мне верить на слово, show me the code!

``` swift
import SwiftUI
 
struct Datas {
//class Datas {
 
    var int: Int
    var string: String
 
    internal init(int: Int, string: String) {
        self.int = int
        self.string = string
    }
 
}
 
struct StateExample: View {
    @State private var datas = Datas(int: 1, string: "String")
    var body: some View {
        VStack(alignment: .center, spacing: 14) {
            Text("datas int: \(datas.int)")
            Button("Change int") {
                datas.int += 1
            }
 
            Text("datas string: \(datas.string)")
            Button("Change string") {
                datas.string += "."
            }
        }
    }
}
 
struct StateExample_Previews: PreviewProvider {
    static var previews: some View {
        StateExample()
    }
}
```

Нажатие на кнопки приводит к ожидаемым изменениям, только если Datas — struct, если же Datas сделать class — изменение полей класса не приводит к изменению всей переменной datas, и код, стоящий за propertyWrapper @State, не подхватит изменение объекта и не выполнит повторное вычисление переменной body.

**Таким образом используем @State:**

-   для того, чтобы хранить внутреннее состояние View, которое не надо сохранять между сессиями работы приложения. К примеру, у View, которая является кастомной кнопкой, можно добавить флаг — нажата кнопка или нет, подразумевая, что, если мы создаем кнопку, — она всегда в значении по умолчанию. Или для активного id — элемент списка. Обычно при заходе на экран со списком ни один элемент не выделен, и это не задается снаружи.
-   также очень часто @State используют как черновик, во время прототипирования экрана, чтобы впоследствии перенести переменную в тот же ObservedObject.

## @Binding

Со @State вроде все понятно, но как передавать значение переменных, объявленных как State, внутренним компонентам, чтобы дети могли их изменять и чтобы изменения отражались и в родительской View? (мы же за модульную структуру).

Для этого и была создана обертка [@Binding](https://developer.apple.com/documentation/swiftui/binding), чтобы установить двустороннюю связь в плане данных состояния View между родительской View и ее ребенком.

Заглянем в документацию, или, чтобы ускорить процесс, можно воспользоваться инструментом Jump to Definition в Xcode. Если навести курсор мыши над словом @State в Xcode, нажать на клавиатуре ⌃ + ⌘ и нажать левую кнопку (по факту выполнить Jump to Definition), то мы увидим документацию по State прямо внутри Xcode. Вообще рекомендую почаще заглядывать в документацию.

Благодаря этой документации можно убедиться, что projectedValue имеет тип Binding<Value> (дополнительную информацию по projectedValue можно получить из прошлого [поста](https://blog.noveogroup.ru/2020/11/property-wrappers-v-swift/)).

В приведенном ниже примере read/write-доступ имеют как parent view (BindingExample), она отображает имя и может его обнулить с помощью кнопки Reset, так и child view ChildTextControl, которая в свою очередь делегирует изменение имени в системный контрол TextField:

```Swift
	
import SwiftUI
 
struct BindingExample: View {
    @State private var name = ""
    var body: some View {
        VStack(alignment: .center, spacing: 14) {
            Text("Current name: \(name)")
            
            Button("Reset") {
                name = ""
            }.disabled(name.count == 0)
 
            ChildTextControl(text: $name)
 
            Spacer()
        }.padding([.top, .bottom])
    }
}
 
struct ChildTextControl: View {
 
    @Binding var text: String
 
    var body: some View {
        TextField("Enter name", text: $text)
            .padding()
    }
}
 
struct BindingExample_Previews: PreviewProvider {
    static var previews: some View {
        BindingExample()
    }
}
	
```

	
В примере можно увидеть, что ChildTextController ожидает в конструкторе @Binding var text: String, а мы передаем $name.

В документации можно узнать, что, подставляя символ $ перед State-переменной, мы по факту получаем projectedValue у State, а для State projectedValue имеет тип Binding<Value>, т.е. $name и есть Binding.

И вновь, таки применив Jump to Definition уже на @Binding, мы можем увидеть, что конструктор структуры Binding в качестве параметров принимает замыкания get/set:

```Swift 

public init(get: @escaping () -> Value, set: @escaping (Value) -> Void)

```

Таким образом, Binding — это средство, которое позволяет работать с value-типами как с reference. Ведь если мы передадим Int из одной View в другую — произойдет ее копирование и изменения в parent не будут отражаться в child, впрочем, как и наоборот. А Binding — это фасад, который скрывает, что под капотом он несет не сами данные, а функции, позволяющие читать/писать в оригинальное хранилище данных, где лежит тот же наш Int.

Также из документации можно подсмотреть, что Binding можно инициализировать константой, и полезно это при использовании Preview:

```Swift

public static func constant(_ value: Value) -> Binding<Value>

```

К примеру, Preview к нашему компоненту ChildTextControl мог бы выглядеть так:

```Swift

struct ChildTextControl_Previews: PreviewProvider {
    static var previews: some View {
        ChildTextControl(text: .constant("test"))
    }
}

```

Ну и если @State-переменная хранит какую-то структуру со своими полями (как вышеприведенная struct Datas), то можно передавать ее ребенку не целиком, а только нужное поле с помощью того же $ с указанием нужного поля:

```Swift

ChildTextControl(text: $datas.string)

```

**Таким образом, область применения @Binding:**

-   передать доступ переменных, обозначенных как @State / @Published, внутрь дочерних компонентов.

## Протокол ObservableObject

Обертки @StateObject, @EnvironmentObject, @ObservedObject будут работать с классами, реализующими протокол ObservableObject, вот его определение:

``` Swift

@available(iOS 13.0, macOS 10.15, tvOS 13.0, watchOS 6.0, *)
public protocol ObservableObject : AnyObject {
 
    /// The type of publisher that emits before the object has changed.
    associatedtype ObjectWillChangePublisher : Publisher = ObservableObjectPublisher where Self.ObjectWillChangePublisher.Failure == Never
 
    /// A publisher that emits before the object has changed.
    var objectWillChange: Self.ObjectWillChangePublisher { get }
}

```

Из определения протокола видно, что реализовать его могут только классы; по сути классы, реализующие этот протокол, будут являться полноценными контейнерами для данных, хранить данные бизнес-логики, а не внутреннее состояние View (как @State).

И работать можно будет с каждым свойством отдельно за счет того, что у каждого свойства мы будем проставлять @Published, что под капотом использует фреймворк Combine. Как указано в документации, для ObservableObject определено свойство objectWillChange, которое будет генерировать событие **перед** каждым изменением свойств, помеченных как @Published.

И если бы мы использовали ObservableObject напрямую, то код мог бы выглядеть как-то так:

```Swift

import UIKit
import Combine
 
var cancellables = Set<AnyCancellable>()
 
class Product: ObservableObject {
    @Published var title: String
    @Published var price: Double
 
    init(title: String, price: Double) {
        self.title = title
        self.price = price
    }
 
    func increasePrice(by value: Double) -> Double {
        price += value
        return price
    }
 
}
 
let product = Product(title: "Phone", price: 100.00)
product.objectWillChange
    .sink { _ in
        print("price '\(product.price)' will change")
    }
    .store(in: &cancellables)
 
print(product.increasePrice(by: 50))

```

Это выведет в консоль 100, а не 150, на то и willChange, а не didChange:

```Swift
price '100.0' will change
150.0

```

Мы также можем с помощью Combine подписаться и на изменение конкретного поля:

```Swift

product.$price.sink { value in
    print("direct $price access: price '\(product.price)' will change")
}.store(in: &cancellables)

```

Если вставить этот код перед print(product…), то в консоли будет

```Swift

direct $price access: price '100.0' will change
price '100.0' will change
direct $price access: price '100.0' will change
150.0

```

Так как на момент подписки на $price там уже было значение — мы тут же его получаем, а следующий print из product.$price.sink отработает уже во время увеличения price. Убедиться в этом можно, закомментировав print(product.increasePrice(by: 50)); таким образом, хоть мы и вообще не изменяем объект product — все равно подписка product.$price.sink отработает, напечатав при этом в консоль одну строку:

```Swift

direct $price access: price '100.0' will change

```

В принципе нам никто не запрещает в классе, реализующем ObservableObject, самим генерировать новые события в objectWillChange (хоть по таймеру) при необходимости.

Но мы в основном будем сталкиваться с ObservableObject именно в связке с SwiftUI, и мы будем напрямую работать со свойствами объектов, реализующих ObservableObject, а события из objectWillChange будет перехватывать сам SwiftUI для того, чтобы знать, что надо перерисовать View. По всей видимости, именно для оптимизации эффективности генерируется willSet, а не didSet, так как это позволяет накапливать изменения и обновлять View реже.

Что же, рассмотрим первую обертку, работающую с ObservableObject, — ObservedObject.

## @ObservedObject

Документация довольно немногословна и говорит, что [@ObservedObject](https://developer.apple.com/documentation/swiftui/observedobject) — это обертка, которая подписывается на объект ObservableObject и обновляет View, когда данные объекта меняются. По сути, это мост между данными, хранящимися в ObservableObject, и нашими View.

Кстати, при выходе SwiftUI нам была доступна только эта обертка, @StateObject была добавлена позже (в так называемом SwiftUI 2.0, представленном на WWDC 2020), давайте на этом примере поймем, почему пришлось добавить еще одну обертку.

```Swift
import SwiftUI
 
class AppState: ObservableObject {
    @Published var counter: Int = 0
}
 
struct ObservedObjectExample: View {
    @State private var mainCounter = 0
    var body: some View {
        VStack(alignment: .center, spacing: 20) {
            Text("Main counter: \(mainCounter)")
                .font(.title)
            Button("Increase main") {
                mainCounter += 1
            }
 
            Divider().padding()
 
            CounterView()
        }.padding()
    }
}
 
struct CounterView: View {
    @ObservedObject var appState = AppState()
 
    var body: some View {
        VStack(alignment: .center, spacing: 20) {
            Text("Child counter: \(appState.counter)")
                .font(.title)
            HStack(spacing: 20) {
                Button("Increase main") {
                    appState.counter += 1
                }
                
                Button("Decrease") {
                    appState.counter = max(0, appState.counter - 1)
                }
                .disabled(appState.counter == 0)
            }
        }
    }
}
 
struct ObservedObjectExample_Previews: PreviewProvider {
    static var previews: some View {
        ObservedObjectExample()
    }
}

```

Во View верхнего уровня ObservedObjectExample мы отображаем, как @State-счетчик mainCounter (в Text), так и ребенка CounterView, у которого внутри создается переменная типа AppState с указанной оберткой @ObservedObject.

На первый взгляд, проблем нет никаких, мы можем нажать кнопку «Increase main» для Main counter, и это честно увеличит @State private var mainCounter, обновив ObservedObjectExample. Мы можем нажать Increase/Decrease для ребенка CounterView, что изменит данные в переменной AppState, и SwiftUI честно перерисует CounterView. Где подвох?

А подвох в том, что если еще раз нажать «Increase main» для Main counter, счетчик Child counter обнулится.

Почему так случилось? На самом деле все просто: при нажатии на «Increase main» меняется mainCounter, что вызывает пересчет переменной body для ObservedObjectExample, а это в свою очередь вызывает пересоздание CounterView. А при повторном создании CounterView у нас вновь инициализируется переменная appState со счетчиком counter = 0. Если не ожидать этого — неожиданное пересоздание переменной может стать очень неприятным сюрпризом.

Таким образом, сферой применения @ObservedObject можно было бы считать:

-   если вам нужно, чтобы происходило пересоздание состояния. Хотя тяжело представить, зачем такое может быть нужно, так как одно дело, когда это ожидаемое поведение (переход со списка List в DetailView), а другое дело — приведенный выше пример, когда дочерний компонент неожиданно сбрасывает свое состояние.
-   если вы уверены, что переменная никогда не будет уничтожена, создаем, к примеру, на старте приложения внутри того же WindowGroup.

Но как будет пояснено в разделе с @StateObject, даже это не стоит делать.

**Остается одно применение @ObservedObject:**

-   если вам надо уже созданную переменную класса, реализующего ObservableObject, передать вниз по иерархии.

## @StateObject

После WWDC 2020 нам добавили еще одну обертку — [@StateObject](https://developer.apple.com/documentation/swiftui/stateobject), спасителя от пересоздания переменной при перерисовке View.

Для того, чтобы починить баг со сбросом состояния дочерней View при увеличении счетчика родительской, достаточно в CounterView сменить @ObservedObject на @StateObject.

Вернемся к теории: в документации для **@StateObject** написано «A property wrapper type that **instantiates** an observable object.», в то время как для **@ObservedObject** «A property wrapper type that **subscribes** to an observable object and invalidates a view whenever the observable object changes.»

То есть Apple прямо говорит: не стоит создавать самим ObservedObject внутри View, которое будет его использовать, создавать нужно только StateObject, а уже в дочерних View определять переменную как @ObservedObject.

Проследить путь appState и убедиться, что все причастные View работают с одним и тем же объектом appState, можно в этом примере:

```Swift
import SwiftUI
 
class AppState: ObservableObject {
    @Published var counter: Int = 0
}
 
struct StateObjectTestView: View {
    @StateObject private var appState = AppState()
    var body: some View {
        NavigationView {
            List {
                Section(header: Text("Observed Object")) {
                    NavigationLink(
                        destination: NestedObservedObjectExample(state: appState),
                        label: {
                            Text("Nested ObservedObject Example")
                        })
                }
            }
        }
    }
}
 
struct NestedObservedObjectExample: View {
    @ObservedObject var state: AppState
    var body: some View {
        VStack(alignment: .center, spacing: 20) {
            Text("Main counter: \(state.counter)")
                .font(.title)
            Button("Increase main") {
                state.counter += 1
            }
 
            Divider().padding()
 
            NestedCounterView(appState: state)
        }.padding()
    }
}
 
struct NestedCounterView: View {
    @ObservedObject var appState: AppState
 
    var body: some View {
        VStack(alignment: .center, spacing: 20) {
            Text("Child counter: \(appState.counter)")
                .font(.title)
            HStack(spacing: 20) {
                Button("Increase") {
                    appState.counter += 1
                }
 
                Button("Decrease") {
                    appState.counter = max(0, appState.counter - 1)
                }
                .disabled(appState.counter == 0)
            }
        }
    }
}
 
struct StateObjectTestView_Previews: PreviewProvider {
    static var previews: some View {
        StateObjectTestView()
    }
}

```

Видно, что в корневой View (а можно было и в WindowGroup) мы определяем переменную как @StateObject, а во всех дочерних — как @ObservedObject, и где бы мы ни меняли appState.counter, — данные будут обновлены во всех View.

Важно отметить, что @StateObject привязывается к конкретному экземпляру View, не к типу View.

**Область применения @StateObject:**

-   создавать объекты с данными внутри View, будучи уверенным, что они не обнулятся при перерисовке этого View. И это важный момент, если же пересоздастся родительская View (вернулись по навигационному стеку назад и зашли снова на родительскую View, к примеру), то уже пересоздадутся и дочерние View, соответственно пересоздадутся и дочерние переменные, хоть они и @StateObject. Т.е. не стоит думать, что если мы пометили переменную как @StateObject, то она вообще никогда не пересоздастся, это работает только в рамках пересоздания внутри body родительской View.

## @EnvironmentObject

Практически Dependency Injection из коробки. По сути мало чем отличается от ObservedObject, в том смысле, что parent создает переменную, а дочерняя View получает к этой переменной доступ. Разница в том, что если эта переменная прикреплена к родительской View, все дети, дети детей и т.д. получают к ней доступ. Особенно это удобно, если эта переменная нужна только на самых нижних уровнях, т.к. нет необходимости прокидывать через все View посредники. Есть подводный камень: не всегда ясно, будет ли передан environmentObject для дочерних View, созданных посредтвом alert, sheet, navigationLink. На WWDC 2021 разработчики Apple рекомендовали для этих случаев проставлять вручную environmentObject.

_Original Question:_ I’ve had several intermittent crashes from environment objects being nil when I pass them to a sheet or NavigationLink. It’s tricky to replicate due to being intermittent and I usually work around it by architecting my code differently to avoid passing environment objects. Do you know of reasons this might happen? All I can think of is that the views that originate the environmentObject further up the view hierarchy are being taken out of memory. Thanks for any help you can provide!

_Answer (engineer #1):_ NavigationLink by design doesn’t flow EnvironmentObjects through to its destination as it’s unclear where the environmentObject should be inherited from. I suspect this might what’s causing your issue. In order to get the behavior you expect, you’ll have to explicitly pass the environmentObject through at that point.

_Answer (engineer #2):_ You can also apply the environmentObject to the NavigationView itself, which will make it available to all pushed content.

``` Swift 

struct ContentView: View {
    @StateObject private var appState = AppState()
    var body: some View {
        NavigationView {
            List {
                ...
                Section(header: Text("Environment Object")) {
                    NavigationLink(
                        destination: EnvironmentObjectExample()
                            .environmentObject(appState),
                        label: {
                            Text("EnvironmentObject Example")
                        })
                }
            
}     
 
 ``` 

``` Swift

import SwiftUI
 
struct EnvironmentObjectExample: View {
    var body: some View {
        VStack {
            Text("Main")
            Child1EnvironmentObjectExample()
        }
    }
}
 
struct Child1EnvironmentObjectExample: View {
    var body: some View {
        VStack {
            Text("Child1")
            Child2EnvironmentObjectExample()
        }
    }
}

struct Child2EnvironmentObjectExample: View {
    @EnvironmentObject var appState: AppState
    
    var body: some View {
        VStack {
            Text("Child2")
            Text("Environment counter: \(appState.counter)")
                .font(.title)
            Button("Increase main") {
                appState.counter += 1
            }
        }
    }
}

```

Из примера можно извлечь следующее:

-   чтобы проставить environmentObject, нужно для корневой View проставить .environmentObject(<object>);
-   получать доступ можно в любой дочернeй View на любой глубине с помощью

```Swift
@EnvironmentObject var varName: Type 
```

-   создавать объекты для environment также стоит с помощью @StateObject. Но нужно быть очень аккуратным, т.к. если мы забыли проставить .environmentObject(object) — при попытке открыть View, использующее отсутствующий EnvironmentObject, вылетит Fatal error.

Также естественным ограничением является то, что можно положить в Environment только один объект определенного типа для конкретной иерархии View, т.к. доступ идет по типу, а не по имени (.environmentObject(<object>)).

**Область применения @EnvironmentObject:**

-   если объект используется детьми View и нужен всего 1 объект данного типа, особенно если объект нужен не всем View в цепочке создания, а где-то глубоко внизу в цепочке созданных View, чтобы не передавать постоянно ObservedObject явно от родителя к ребенку, раз уж большинству View это все равно это не нужно.

**Про остальные обертки вкратце:**

Есть также обертки для частных случаев. Подробно я их разбирать не буду, просто упомяну:

-   @AppStorage, по сути прокси для UserDefaults,
-   @FetchRequest, позволяет получить доступ к CoreData объектам из View,
-   @SceneStorage, в основном используется для state restoration, чтобы после перезапуска приложения мы могли показать приложение в том виде, в котором оно находилось перед закрытием (положение, позиция внутри экрана и т.д.).