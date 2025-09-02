## Checkpoint 7 
Your challenge is this: make a class hierarchy for animals, starting with Animal at the top, then Dog and Cat as subclasses, then Corgi and Poodle as subclasses of Dog, and Persian and Lion as subclasses of Cat.

But there’s more:

The Animal class should have a legs integer property that tracks how many legs the animal has.
The Dog class should have a speak() method that prints a generic dog barking string, but each of the subclasses should print something slightly different.
The Cat class should have a matching speak() method, again with each subclass printing something different.
The Cat class should have an isTame Boolean property, provided using an initializer.

```swift
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
```
