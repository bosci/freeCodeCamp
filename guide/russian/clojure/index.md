---
title: Clojure
localeTitle: Clojure
---
## Начало работы с Clojure

Прежде чем мы начнем, вы можете [установить Clojure](http://clojure.org/guides/getting_started) и [Leiningen](http://leiningen.org/#install) (который является инструментом для управления проектами в Clojure). Это позволит вам запустить Clojure в командной строке с помощью REPL (Read-Evaluate-Print-Loop).

## Определение переменных

Хлеб и масло любого языка программирования являются переменными и функциями. Определим переменную!
```
(def our-string "Hello world!") 
```

Очень просто. Этот фрагмент кода использует макрос `def` чтобы связать строку ( `"Hello world!"` ) С символом ( `our-string` ). Мы также могли бы определить число, такое как `1` или `1.1` , символ, например `\a` или `\Z` , или нечто более сложное, как список или регулярное выражение ( _uuuugh_ ).

Обратите внимание, что наш код находится в круглых скобках, например, в списке, потому что все в Lisp - это список! (Это будет очень важно, когда мы начнем говорить о макросах.)

## Определение функций

Теперь давайте определим функцию!
```
(defn hello-world [] (println our-string)) 
```

Это немного сложнее. Как и `def` , он использует макрос ( `defn` ) для создания переменной - хотя на этот раз эта переменная является функцией. Пустой вектор (вектор - это тип списка - думайте об этом как массив) после того, как `hello-world` определяет аргументы этой функции - в этом случае у нас их нет. После этого код выполняет функцию. Он оценивает `our-string` , которая равна `"Hello world!"` , и печатает его на консоли. Давайте запустим его!
```
(hello-world) 
 ; => Hello world! 
 ;    nil 
```

Вы также можете написать следующее:
```
(def hello-world (fn [] (println our-string))) 
```

`defn` - это просто ярлык, который поможет сохранить ваш код кратким. `(defn ...)` и `(def ... (fn ...))` одинаковы на практике.

## параметры

Ну, это было хорошо, но это было не очень интересно. Попробуем функцию с параметрами. Как насчет того, что добавляет 3 номера?
```
(defn add [xyz] (+ xyz)) 
 (add 1 2 3) 
 ; => 6 
```

…Оставайтесь на линии. `(+ xyz)` ? Это выглядит смешно. Ну, Lisps написаны с использованием «префиксной нотации», что означает, что функция всегда на первом месте. Так как все математические операторы в Lisp ( `+ - * /` ) являются справедливыми функциями, они также выходят перед их аргументами (в данном случае `xyz` ).

Вы заметите, что у нашего вектора сейчас есть кое-что: `[xyz]` ! Всякий раз, когда функция имеет параметры, вы определяете их в этом векторе рядом с именем функции.

### деструктурирующие

Отличная характеристика аргументов в Clojure - разрушение. Это позволяет вам «вытаскивать» элементы из списка.
```
(defn add [[xy] z] (+ xyz)) 
 (add [1 2] 3) 
 ; => 6 
```

![:rocket:](//forum.freecodecamp.com/images/emoji/emoji_one/rocket.png?v=2 ": Ракета:") [IDEOne!](https://ideone.com/SWlvKn)

Аргументами этой функции являются коллекция ( `[xy]` ) и число ( `z` ). Мы можем использовать деструктуризацию, чтобы вытащить первый и второй элементы из списка и называть их `x` и `y` .

### Функции с любым количеством параметров

Вы также можете определить функцию с произвольным числом аргументов, используя `&` .
```
(defn demonstrate-rest [first & rest] 
  (println first) 
  (println rest)) 
 (demonstrate-rest 1 "foo" ["bar" 22]) 
 ; => 1 
 ;    ("foo" ["bar" 22]) 
 ;    nil 
```

![:rocket:](//forum.freecodecamp.com/images/emoji/emoji_one/rocket.png?v=2 ": Ракета:") [IDEOne!](https://ideone.com/VftymP)

Как вы можете видеть, используя `&` отделили аргументы нашей функции в одну переменную, называемую `first` и список переменных, называемых `rest` . Это означает, что наша функция может иметь любое количество аргументов!

## возврате

Возможно, вы заметили какие-то странные вещи. Всякий раз, когда мы используем `println` , кажется, что `nil` появляется в нашем выпуске. Кроме того, наша функция `add` возвращает `6` , но мы никогда не говорили ей возвращать что-либо.

В Clojure возвраты являются «неявными». Если вы использовали Ruby, вы, вероятно, знакомы с этой концепцией. Вместо того, чтобы сообщать нашей функции о возврате чего-либо, он оценивает весь код внутри своего тела и возвращает результат. Например, наша функция `add` оценивает `(+ xyz)` , а затем возвращает этот результат.

Причина, по которой наши функции, использующие вывод `println` `nil` заключается в том, что `println` оценивает значение `nil` . ( `nil` как `null` или `None` - ничего не представляет).

| [![:point_left:](//forum.freecodecamp.com/images/emoji/emoji_one/point_left.png?v=2 ": Point_left:") Предыдущая](//forum.freecodecamp.com/t/what-is-clojure/18419) | [![:book:](//forum.freecodecamp.com/images/emoji/emoji_one/book.png?v=2 ":книга:") Главная ![:book:](//forum.freecodecamp.com/images/emoji/emoji_one/book.png?v=2 ":книга:")](//forum.freecodecamp.com/t/clojure-resources/18422) | [следующий ![:point_right:](//forum.freecodecamp.com/images/emoji/emoji_one/point_right.png?v=2 ": Point_right:")](//forum.freecodecamp.com/t/clojure-conditionals/18412) |  
| [Резюме](//forum.freecodecamp.com/t/what-is-clojure/18419) | [Содержание](//forum.freecodecamp.com/t/clojure-resources/18422) | [Условные](//forum.freecodecamp.com/t/clojure-conditionals/18412) |