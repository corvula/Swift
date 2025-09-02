import Foundation

func readDouble(prompt: String) -> Double {
    print(prompt, terminator: "")
    if let input = readLine(), let value = Double(input) {
        return value
    }else {
        print("Непраивильно введені дані, щодо доща, спробуйте ще раз")
        return readDouble(prompt: prompt)
    }
}
func readInt(prompt: String) -> Int {
    print(prompt, terminator: "")
    if let input = readLine(), let value = Int(input) {
        return value
    }else {
        print("Непраивильно введені дані, щодо доща, спробуйте ще раз")
        return readInt(prompt: prompt)
    }
}

func expectedUtility(probRain: Double, rainScore: Int, sunScore: Int) -> Double {
    return probRain * Double(rainScore) + (1 - probRain) * Double(sunScore)
}

let raitRain: Double = readDouble(prompt: "🌧️ Введіть ймоврінсть дощу від 0 до 1:")

let homeRain: Int = readInt(prompt: "🌨️🏠 Введіть оцінку дощової погоди, коли Ви вдома від 1 до 10: ")
let homeSun: Int = readInt(prompt: "☀️🏠Введіть оцінку сонячної погоди, коли Ви Вдома від 1 до 10: ")
let outRain: Int = readInt(prompt: "🌨️🏃‍♀️‍➡️Введіть оцінку дощової погоди, коли Ви на вулиці від 1 до 10: ")
let outSun: Int = readInt(prompt: "☀️🏃‍♀️‍➡️Введіть оцінку сонячної погоди, коли Ви на вулиці від 1 до 10: ")

let userHome = expectedUtility(probRain: raitRain, rainScore: homeRain, sunScore: homeSun)
let userOut = expectedUtility(probRain: raitRain, rainScore: outRain, sunScore: outSun)

print("\n📊 Результати:")
print("Очікувана корисність для 'сидіти вдома': \(userHome)")
print("Очікувана корисність для 'вийти на вулицю': \(userOut)")

if userOut > userHome {
    print("🏠 Більше корисна, вийти на вулицю")
} else if userOut < userHome {
    print("🏠 Більше корисна, сидіти вдома")
} else if userOut == userHome {
    print("Зробіть власний вибір)")
}
