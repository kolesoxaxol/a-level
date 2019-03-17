# Урок №3. Типы данных и их приведение

## Полезные ссылки

[Сборка мусора](https://docs.microsoft.com/ru-ru/dotnet/standard/garbage-collection/)

[Структура сборки в .NET](https://metanit.com/sharp/tutorial/10.1.php)

[Тип string](https://docs.microsoft.com/ru-ru/dotnet/csharp/programming-guide/strings/)



## Сборка мусора

![Приложение в памяти](/Module-1/images/app-in-memory.png)

Размещайте объект в управляющей куче с помощью ключевого слова **new** и забывайте об этом.

![Garbage collector](/Module-1/images/garbage-collector.png)

Чем дольше объект находится в куче, тем выше вероятность того, что он там будет оставаться.

- **Поколение 0.** Идентифицируется новый только что размещённый объект, который ещё никогда не помечался как надлежащий удалению в процессе сборки мусора
- **Поколение 1.** Идентифицирует объект, который уже «пережил» один процесс сборки мусора (был помечен, как надлежащий удалению, но не был удалён из-за достаточного свободного места в куче).
- **Поколение 2.** Идентифицирует объект, который пережил более одного прогона сбора мусора

###Корневые элементы приложения

- Ссылки на глобальные объекты (хотя в C# они не разрешены, CIL-код позволяет размещать глобальные объекты
- Ссылки на любые статические объекты или статические поля.
- Ссылки на локальные объекты в пределах кодовой базы приложения.
- Ссылки на передаваемые методу параметры объекта.
- Ссылки на объект, ожидающий финализации.
- Любые регистры центрального процессора, которые ссылаются на объект.

## Тип string

**IMMUTABLE** – попытка изменения создает новую строку!!!!

Reference type, но ведет себя как Value type
Непредсказуемый размер
При копировании создаем новый экземпляр!

***Магии нет**

string s1 = "test1";

string s2 = s1;

Console.WriteLine($"s1: {s1}");
Console.WriteLine($"s2: {s2}");

s2 = "new string";

Console.WriteLine($"s1: {s1}");
Console.WriteLine($"s2: {s2}");

## Методы

Если переменные хранят некоторые значения, то методы содержат собой набор операторов, которые выполняют определенные действия

Общее определение метода выглядит следующим образом:

[модификаторы] тип_возвращаемого_значения название_метода ([параметры])
{
   // тело метода
}

Модификаторы и параметры необязательны.

Рассмотрим на примере метода Main:
static void Main(string[] args)
{
   Console.WriteLine("Привет мир!");
}

Ключевое слово static является модификатором. Далее идет тип возвращаемого значения. В данном случае ключевое слово void указывает на то, 
что метод ничего не возвращает. Такой метод еще называется процедурой.

Далее идет название метода – Main и в скобках параметры – string[] args. И в фигурные скобки заключено тело метода – все действия, которые он выполняет.

Еще примеры определения процедур:
// определение первого метода
static void Method1()
{
   Console.WriteLine("Method1");
}
 
// определение третьего метода
void Method2()
{
   Console.WriteLine("Method2");
}

Функции. В отличие от процедур функции возвращают определенное значение:
int Factorial()
{
   return 1;
}
 
string Hello()
{
   return "Hello World";
}

В функции в качестве типа возвращаемого значения вместо void используется любой другой тип. В данном случае тип int. 
Функции также отличаются тем, что обязательно должны использовать оператор return, после которого ставится возвращаемое значение.

Также стоит отметить, что возвращаемое значение всегда должно иметь тот же тип, что значится в определении функции. 
То есть если функция возвращает значение типа int, поэтому после оператора return стоит число 1 – которое неявно является объектом типа int.

## Приведение типов

Convert.ToInt32() - **опасное**
int.Parse() – **опасное**

bool res = int.TryParse(string s, out val) – **безопасно**!

## Boxing/unboxing

![Boxing](/Module-1/images/boxing.png)

![Unboxing](/Module-1/images/unboxing.png)

![Boxing vs Unboxing](/Module-1/images/boxing-vs-unboxing.png)

## Константы

Значение неизменяемое в рамках фрагмента кода!

const int Const = 5;

![Consts in memory](/Module-1/images/constants-in-memory.png)


## Домашнее задание

Задача: сделать программу для решения квадратных уравнений

![Квадратное уравнение](/Module-1/images/square-equation.png)

1.Члены класса/структуры.
2.Что такое метод (функция)? Какие виды бывают?
3.Посмотреть приведение других типов – int в double и наоборот. Что произойдет?
4.Структура solution в .NET.
5.Почитать про сборку мусора.

