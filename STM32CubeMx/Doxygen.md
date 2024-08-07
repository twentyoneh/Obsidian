
| **Команда**     | **Значение**                                                                                                                                                                                                                               |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| \authors        | Указывает автора или авторов                                                                                                                                                                                                               |
| \version        | Используется для указания версии                                                                                                                                                                                                           |
| \date           | Предназначена для указания даты разработки                                                                                                                                                                                                 |
| \bug            | Перечисление известных ошибок                                                                                                                                                                                                              |
| \warning        | Предупреждение для использования                                                                                                                                                                                                           |
| \copyright      | Используемая лицензия                                                                                                                                                                                                                      |
| \example        | Команда, добавляемая в комментарий для указания ссылки на исходник с примером (добавляется после команды)                                                                                                                                  |
| \todo           | Команда, используется для описания тех изменений, которые необходимо будет сделать (TODO).                                                                                                                                                 |
|                 |                                                                                                                                                                                                                                            |
| **Обозначение** | **Значение**                                                                                                                                                                                                                               |
| <...>           | Угловые скобки показывают, что аргумент представляет собой одно слово                                                                                                                                                                      |
| (...)           | Круглые скобки показывают, что аргументом является весь текст вплоть до конца строки, на которой размещена команда                                                                                                                         |
| {...}           | Фигурные скобки показывают, что аргументом является весь текст вплоть до до следующего параграфа. Параграфы разделяются пустой строкой или [командой-разделителем](http://www.stack.nl/~dimitri/doxygen/manual/commands.html#cmdattention) |

```
\param [<направление>] <имя_параметра> {описание_параметра}
```

```
/*!Копирует содержимое из исходной области памяти в целевую область память\param[out] dest Целевая область памяти\param[in] src Исходная область памяти\param[in] n Количество байтов, которые необходимо скопировать*/void memcpy(void *dest, const void *src, size_t n);
```
![[Pasted image 20240708174040.png]]
 Возвращаемое значение
 ```
\return {описание_возвращаемого_значения}
```

```
/*!Находит сумму двух чисел\param a,b Складываемые числа\return Сумму двух чисел, переданных в качестве аргументов*/double sum(const double a, const double b);
```
![[Pasted image 20240708174126.png]]
###### **Исключения**

  
Для указания исключения используется команда _\throw_ (или её синонимы: _\throws_, _\exception_), которая имеет следующий формат:
```
\throw <объект-исключение> {описание}
```
```
\throw std::bad_alloc В случае возникновения ошибки при выделении памяти
```


##### **Документирование перечислений**

  
Документирование перечислений не сильно отличается от документирования других элементов. Рассмотрим пример, в котором иллюстрируется то, как можно удобно документировать их:  
  

```
/// Набор возможных состояний объектаenum States {         Disabled, ///< Указывает, что элемент недоступен для использования         Undefined, ///< Указывает, что состояние элемента неопределенно         Enabled, ///< Указывает, что элемент доступен для использования}
```
