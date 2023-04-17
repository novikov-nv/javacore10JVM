# javacore10JVM

Metaspace - хранит информацию о JvmComprehension.class, Object.class, Integer.class, System.class,
(их имена, методы, поля и т.д)

Classloaders: происходит загрузка классов на уровне Bootstrap, т.к. все классы являются базовыми.

0. Выполнение метода main():
- в стеке выделяется место - фрейм для хранения значений всех переменных, связанных с этим методом
1. В стеке в фрейме main сохраняется примитивная переменная int i = 1
2. Выделяется память в куче под объект Object
- создается переменная и ей присваевается адресс объекта Object
- выделяется память в стеке фрейма main
3. аналогично п.2 т.к. используется автоупаковка примитивного типа данных в класс-оболочку
4. создается новый фрейм для метода printAll()
- для переданных параметров в метод создаются переменные и выделяется место в стеке
- присваиваются им ссылки на используемые объекты
(т.к. из одного фрейма в другом их не видно)
5. создается новый объект Integer в памяти кучи и присваивается ссылка на переменную uselessVar в фрейме printAll
6. в фрейме printAll создается новый фрейм метода println() в который передаются ссылки на "o", "i", "ii"
-в этом же фрейме создается новый для метода toString()

Сборщик мусора после выполнения кода printAll(o, i, ii); // 4
может произвести очистку кучи,а именно удалить все объекты,т.к далее в коде они не используются

7. в фрейме main создается фрейм для метода println() с переменной по умолчанию, 
имеющий ссылку на объект в куче с текстом "finished"



