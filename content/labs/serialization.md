---
title: "2. Сериализация"
---

Примеры из лекций и входной код для выполнения заданий находится в репозитории [https://github.com/AltmanEA/edu-serialization](https://github.com/AltmanEA/edu-serialization).

Перед выполнением прочитайте замечания по порядку выполнения заданий и поиску информации из первой работы.

1. Библиотека jackson
   
   1. Изучите документацию к классу ```SimpleDateFormat``` и создайте формат, который бы выводил дату в таком виде: ```2021.01.22```. Создайте объект типа ```ObjectMapper``` и установите его свойство ```dateFormat``` равным созданному формату.
   2. Создайте класс ```Lesson``` со свойствами ```name: String``` и ```date: Date```. Создайте объект этого класса со свойствами, указанными ниже, и выполните его сериализацию в формат JSON. В результате должно получиться примерно следующее:
   <pre><code>{"name":"Java Date","date":"2021.01.22"}</pre></code>
   3. Добавьте аннотацию ```@JsonFormat``` к свойству ```date: Date``` с такими аргументами, чтобы установить формат вывода даты в виде: ```"22.01.2021"``` и выполните еще раз сериализацию объекта из предыдущего пункта.
   4. Определите, какой формат будет использоваться при одновременном использовании двух способов задания формата данных.
   
2. Библиотека kotlinx.serialization

   1. Создайте класс ```Course``` с свойствами ```name: String``` и ```person: Person?```. Создайте объект этого класса со свойствами ```Math``` и ```Person("Leonard Euler")``` и переведите его в формат Json.
   2. Используя аннотацию ```@SerialName``` настройте преобразование, чтобы объект выводился в таком виде:
   <pre><code>{"name":"Math","tutor":{"firstname":"Leonard","surname":"Euler"}}</pre></code>
   3. Декодируйте из строки ```"{\"name\": \"Phys\"}"``` формата Json объект типа ```Course``` и распечатайте полученный объект (сделайте ```Course``` классом данных).
   4. На основе полученных результатов сделайте выводы о том, как обрабатываются ```null-типы```.
   
3. Настройка сериализации

   1. Создайте класс перечисления ```WeekType``` для типа недель учебного плана с возможными значениями: ```TRAINING, SESSION, HOLIDAY```.
   2. Сериализуйте следующий массив:
   <pre><code>arrayListOf(
      1 to WeekType.TRAINING,
      2 to WeekType.TRAINING,
      3 to WeekType.SESSION,
      4 to WeekType.HOLIDAY
   )</pre></code>
   3. Создайте класс ```Week``` со свойствами ```number: Int``` и ```type: WeekType```, преобразуйте массив из предыдущего пункта в массив элементов типа ```Week``` и сериализуйте его.
   4. Создайте ```object WeekTypeSerializer : KSerializer<WeekType>```, который заменял бы типы недель на ```"Обучение", "Сессия" и "Каникулы"``` соответственно. Укажите его для использования для свойства ```type: WeekType``` и сериализуйте снова массив из предыдущего пункта.