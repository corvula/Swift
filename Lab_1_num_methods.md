## Лабораторна 1, Теорія похибок і комп’ютерна арифметика

```swift

import Foundation

func taylorSeries(_ x: Double, _ n: Int) -> Double {
    guard x > 0 else {
        print("x must be greater than 0")
        return 0.0
    }
    
    var sum = 1.0
    var term = 1.0
    
    for i in 1...n {
        term *= -x / Double(i)
        sum += term
    }
    
    return sum
}

func noTaylorSeries(_ x: Double, _ n: Int) -> Double {
    guard x > 0 else {
        print("x must be greater than 0")
        return 0.0
    }
    
    var sum = 1.0
    var term = 1.0
    
    for i in 1...n {
        term *= x / Double(i)
        sum += term
    }
    
    return 1.0 / sum
}

func readX() -> Double? {
    print("Enter the value for x (x > 0):", terminator: " ")
    if let input = readLine(), let x = Double(input), x > 0 {
        return x
    } else {
        print("Invalid input. Please enter a valid number greater than 0.")
        return nil
    }
}

func readN() -> Int? {
    print("Enter the number of terms n (integer):", terminator: " ")
    if let input = readLine(), let n = Int(input), n > 0 {
        return n
    } else {
        print("Invalid input. Please enter a valid positive integer.")
        return nil
    }
}

func runCalculations() {
    guard let x = readX(), let n = readN() else {
        return
    }
    
    let taylorResult = taylorSeries(x, n)
    let noTaylorResult = noTaylorSeries(x, n)

    print("\n--- Results ---")
    print("x = \(x)")
    print("n = \(n)")
    print("Value calculated using Taylor series: \(taylorResult)")
    print("Value calculated using 1/e^x: \(noTaylorResult)")

}

runCalculations()

```
<img width="371" height="158" alt="Знімок екрана 2025-09-08 о 2 36 52 пп" src="https://github.com/user-attachments/assets/51634836-5639-49be-b82a-214cae99f080" />
