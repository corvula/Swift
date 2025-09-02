## CheckPoint 8 

Your challenge is this: make a protocol that describes a building, adding various properties and methods, then create two structs, House and Office, that conform to it. Your protocol should require the following:

A property storing how many rooms it has.
A property storing the cost as an integer (e.g. 500,000 for a building costing $500,000.)
A property storing the name of the estate agent responsible for selling the building.
A method for printing the sales summary of the building, describing what it is along with its other properties.

```swift 
protocol Builders {
    var rooms: String { get set }
    var cost: Int { get set }
    var nameAgent: String { get set }
    
    func salesSummary() -> String
}

struct House: Builders {
    var rooms: String
    var cost: Int
    var nameAgent: String
    
    func salesSummary() -> String {
        print(nameAgent + " is selling " + rooms + " for $" + String(cost))
        return "\(nameAgent) is selling \(rooms) for $ \(cost)"
    }
}
struct Office: Builders {
    var rooms: String
    var cost: Int
    var nameAgent: String
    
    func salesSummary() -> String {
        print(nameAgent + " is selling " + rooms + " for $" + String(cost))
        return "\(nameAgent) is selling \(rooms) for $ \(cost)"
    }
}
var house = House(rooms: "3 Bedrooms", cost: 1000000, nameAgent: "John")
print(house.salesSummary())

var office = Office(rooms: "5 Bedrooms", cost: 2000000, nameAgent: "John")
print(office.salesSummary())   
```

