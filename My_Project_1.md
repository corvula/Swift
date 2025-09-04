## Challenge day 19

You need to create an application that handles unit conversions: users will select input and output units, then enter values, and view the conversion result.

The choice of units is up to you, but you can choose one of the following:

Temperature conversion: users select Celsius, Fahrenheit, or Kelvin.
Length conversion: users select meters, kilometers, feet, yards, or miles.
Time conversion: users select seconds, minutes, hours, or days.
Volume conversion: users select milliliters, liters, cups, pints, or gallons.
If you are going to convert length, you might have:

A segmented control for meters, kilometers, feet, yards, or miles as the input unit.
A second segmented control for meters, kilometers, feet, yards, or miles as the output unit.
A text field where users enter a number.
A text view that displays the result of the conversion.
So if you chose meters as the source unit and feet as the output unit, and then entered 10, you would see 32.81 in the output.

```swift
import SwiftUI // iмпортує фреймворк

struct ContentView: View { // оголошення структури, що працює з протокол для представлення (View)
    
    @State private var inputValue = 0.0 // дефолтне значення для обчислення вхідного
    @State private var inputLength = "metres"//дефолтні значення для вводу
    @State private var outputLength = "kilometres" //поставила дефолтні значення для виводу
    
    private let Length = ["metres", "kilometres", "yards", "feet", "miles"] // масив для вибору вхідної та вихідної систм.вимір
    
    private var convertedValue: Double{ //обчислення для будь-якого з виборів с.в
        
        var ValueInMetres = 0.0
        
        switch inputLength{
        case "kilometres":
            ValueInMetres = inputValue * 1000
        case "feet":
            ValueInMetres = inputValue * 0.3048
        case "yards":
            ValueInMetres = inputValue * 0.9144
        case "miles":
            ValueInMetres = inputValue * 1609.344
        default:
            ValueInMetres = inputValue
        }
        
        var result = 0.0
        
        switch outputLength{
            case "kilometres":
            result = ValueInMetres / 1000
        case "feet":
            result = ValueInMetres / 0.3048
        case "yards":
            result = ValueInMetres / 0.9144
        case "miles":
            result = ValueInMetres / 1609.344
        default:
            result = ValueInMetres
        }
        
        return result
    }
    
    
    
    var body: some View {
        NavigationStack{ // для навігації, що здебільшого зверху
            Form{// для розділення даних
                Section("Input Length"){ //ну тут і так панятна, можна просто перекласти
                    TextField("Length", value: $inputValue, format: .number)
                        .keyboardType(.decimalPad) //тут довго, можу на словах пояснити
                }
                Section("Choose Option for Input"){
                    Picker("Select", selection: $inputLength){
                        ForEach(Length, id: \.self){
                            Text($0)
                        }
                    }
                }
                
                Section("Choose Option for Output"){
                    Picker("Select", selection:$outputLength){
                        ForEach(Length, id: \.self){
                            Text($0)
                        }
                    }
                }
                
                Section("Result"){
                    Text(convertedValue, format: .number)
                }
            }
            .navigationTitle(("Length Converter"))
            .padding()
        }
    }
}


#Preview{ //щоб подивитися, як виглядає
    ContentView()
}

```
### Результат:

<img width="443" height="498" alt="Знімок екрана 2025-09-04 о 9 10 23 пп" src="https://github.com/user-attachments/assets/25523dba-b8d2-4044-b582-684f4e658bdc" />
