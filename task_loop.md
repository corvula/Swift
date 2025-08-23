for i in 1...10{
    if i.isMultiple(of: 2){
        print("\(i)")
    }else{
        print("harosh")
    }
}
 Задачі на for
	1.	Вивести числа від 1 до 10.
	2.	Вивести тільки парні числа від 1 до 20.

 var i = 2
if i > 0 {
    print("Позитивне")
}else if i < 0{
    print("Відʼємне")
}else if i == 0{
    print("Нуль")
}
Написати програму, яка перевіряє число:
	•	якщо воно більше 0 → надрукувати “Позитивне”,
	•	якщо менше 0 → “Негативне”,
	•	якщо дорівнює 0 → “Нуль”.


var count = 0
while count < 5{
    count+=1
    print("\(count)")
}
print("Count is \(count)")

Вивести числа від 1 до 5 за допомогою while.

enum Day{
    case Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday
}
let today: Day = .Sunday
    switch today {
case .Monday, .Tuesday, .Wednesday, .Thursday, .Friday:
    print("Working day")
    case .Saturday, .Sunday:
    print("Weekend")
    }

Створи enum Day з днями тижня (Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday).
За допомогою switch надрукуй:
	•	"Робочий день", якщо день з понеділка по п’ятницю,
	•	"Вихідний", якщо субота або неділя.


