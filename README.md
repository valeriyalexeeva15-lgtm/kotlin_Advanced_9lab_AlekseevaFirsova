# Лабораторная работа №9-10: Продвинутое ООП на Kotlin
## Описание
Лабораторная работа посвящена изучению продвинутых концепций объектно-ориентированного программирования в Kotlin.
** Структура проекта
Проект содержит примеры реализации продвинутых механизмов ООП, а также пояснения к ключевым концепциям.
## Как запустить проект
1. Клонируйте репозиторий:
   bash
   git clone <URL, репозитория»
2. Откройте проект в Intellij IDEA.
3. Запустите любой пример через контекстное меню или напрямую из main
## Автор Алексеева и Фирсова 
## Лицензия
Проект создан в учебных целях.
# Описание изученных тем
## 1. Геттеры и сеттеры
специальные методы для доступа к приватным полям класса, обеспечивающие контроль над чтением и записью данных.
```
class Person {
var age = 0
set(value) {
if (value >= 0) {
field = value
}
}

    val isAdult: Boolean
        get() = age >= 18
}

// Использование
val person = Person()
person.age = 20
println(person.age)      // 20
println(person.isAdult)  // true
person.age = -5         // ничего не произойдёт
```


## 2. Инкапсуляция 
принцип ООП, который объединяет данные и методы работы с этими данными в одном классе, скрывая детали реализации и предоставляя публичный интерфейс для взаимодействия.
class Wallet {
private var money = 1000
```
    fun add(amount: Int) {
        if (amount > 0) money += amount
    }
    
    fun spend(amount: Int): Boolean {
        if (amount <= money) {
            money -= amount
            return true
        }
        return false
    }
    
    fun checkBalance() = money
}
```
## 3.  Data-классы
специальные классы для хранения данных, которые автоматически генерируют полезные методы.
```
// Автоматически создаёт equals, hashCode, toString, copy
data class Student(val name: String, val grade: Int)

// Использование
val student1 = Student("Анна", 5)
val student2 = Student("Анна", 5)

println(student1)                 // Student(name=Анна, grade=5)
println(student1 == student2)     // true
val student3 = student1.copy(grade = 4)  // копия с изменением
```
## 4. Абстрактные классы
классы, которые нельзя инстанциировать напрямую, могут содержать абстрактные методы (без реализации) и обычные методы с реализацией.
```
abstract class Animal {
    abstract fun makeSound()
    
    fun sleep() {
        println("Zzz...")
    }
}
class Dog : Animal() {
    override fun makeSound() {
        println("Гав!")
    }
}
class Cat : Animal() {
    override fun makeSound() {
        println("Мяу!")
    }
}
// Использование
val dog = Dog()
dog.makeSound()  // Гав!
dog.sleep()      // Zzz...
```
## 5. Интерфейсы
определяют контракт поведения, который должны реализовать классы. Могут содержать абстрактные методы и методы с реализацией (default-методы).
```
// Определяем интерфейс видео-плеера
interface VideoPlayable {
fun play()
}
// Определяем интерфейс аудио-плеера
Interface VideoPlayable {
fun play()
}

class MediaPlayer: VideoPlayable, AudioPlayable {
override fun play() {
println("Play audio and video")
}
```
