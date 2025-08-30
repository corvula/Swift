class Animal {
    var legs: Int
    init(legs: Int) {
        self.legs = legs
    }
}
class Cat: Animal{
    var isTame : Bool
    init(isTame: Bool, legs: Int){
        self.isTame = isTame
        super.init(legs: legs)
        if isTame == true {
            print("I can be with u")
        } else {
            print("I can't bite u")
        }
    }
        func speak()  {
            print("Meow!")
        }
}
class Persian: Cat {
    override func speak() {
        print("I'm Persion, Meow!")
    }
}
class Lion: Cat {
    override func speak() {
        print("I'm Lion, Meow!")
    }
}
class Dog:Animal{
    func speak()  {
        print("Woof!")
    }
}
class Corgi: Dog {
    override func speak() {
        print("I'm Corgi, Woof!")
    }
}
class Poodle: Dog {
    override func speak() {
        print("I'm Poodle, Woof!")
    }
}

let dog = Dog(legs: 4)
dog.speak()

let corgi = Corgi(legs: 4)
corgi.speak()

let poodle = Poodle(legs: 4)
poodle.speak()

let persian = Persian(isTame: true, legs: 4)
persian.speak()
print("Persian tame? \(persian.isTame)")

let lion = Lion(isTame: false, legs: 4)
lion.speak()
print("Lion tame? \(lion.isTame)")

chechkpoint 7
