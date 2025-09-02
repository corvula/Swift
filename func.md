## Додаткові завдання для вивчення throws, func

Задача для заданих чисел і отримання з них середнє арифметичне 
```swift
enum MathErorr: Error{
    case divisionByZero
    case negativeNumbersNotAllowed
}

func divided(a : Double, b: Double) throws -> Double{
    if b == 0{
        throw MathErorr.divisionByZero
    } else if a > 0 && b > 0{
        return ((a + b)/2)
    } else{
        throw MathErorr.negativeNumbersNotAllowed
    }
}
do {
    let result = try divided(a: 20, b: 5)
    print("Результат: \(result)")
} catch MathErorr.divisionByZero{
    print("Ділити на нуль не можна!")
} catch MathErorr.negativeNumbersNotAllowed{
    print("Не допускаються negative числа!")
}
```
Задача для заданого пароля, перевірка його, має бути не менше 8 символів, і також містити у собі числа, якщо щось не правильно, виводиться помилка
```swift
enum PasswordError: Error{
    case tooShort
    case noDigit
}

func checkPassword(_ password: String) throws -> String{
    if password.count < 8{
        throw PasswordError.tooShort
    }
    var hasDigit = false
    for char in password{
        if char.isNumber{
            hasDigit = true
            break
        }
    }
    if !hasDigit{
        throw PasswordError.noDigit
    }
    return "Password is valid"
}
do{
    let result = try checkPassword("abc12")
    print(result)
} catch PasswordError.tooShort{
    print("Password is too short")
}catch  PasswordError.noDigit{
    print("Password must contain a digit")
}
```
Задача на перевірку заданого масиву та пошук максимального елементу за допомогою цикла, масив не має бути пустим
```swift
enum ArrayError: Error {
    case empty
}

func maxElement(_ numbers: [Int]) throws -> Int {
    if numbers.isEmpty {
        throw ArrayError.empty
    }
    var maxElement = numbers[0]
    for number in numbers{
        if number > maxElement{
            maxElement = number
        }
    }
    return maxElement
}
let numbers = [1, 2, 3, 4, 5]
do {
    let result = try maxElement(numbers)
    print("Max number is: \(result)")
} catch ArrayError.empty{
    print("array is empty")
}
```
