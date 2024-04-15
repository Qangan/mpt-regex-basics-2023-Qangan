# Знакомство с регулярными выражениями

[![Очередная смешная картинка](https://imgs.xkcd.com/comics/regular_expressions.png)](https://xkcd.com/208)

Для решения каждого из заданий необходимо выписать последовательность команд,
выполняющих то, что требуется в условии, в файл `solution/taskX.sh`,
где `X` - номер соответствующего задания.

<details>
  <summary>Отладка</summary>

Для локальной отладки можно запустить ваше решение с помощью следующей команды:
```console
$ bash -xe solution/taskX.sh
```
Параметры `-xe` (`-x` и `-e`) включают логирование выполненных команд и
завершение исполнения при первой ошибке, что бывает очень полезно при отладке скриптов.
Более подробное описание этих и других опций утилиты `bash` можно получить с помощью
```console
$ bash -c "help set"
```
</details>

## Задание №1

Файл [data/pushkin.txt](/data/pushkin.txt) содержит произведение Александра Пушкина «Капитанская дочка».

Требуется посчитать, сколько раз в данном произведении встречается слово "дверь".

> Вам понадобится [grep](https://linux.die.net/man/1/grep) и [wc](https://linux.die.net/man/1/wc).

## Задание №2

Требуется посчитать, сколько раз в «Капитанской дочке» встречается слово "вина" (например, "... стакан вина и ...").
Причем различные частичные совпадения (например, "винам" или "половина") учитывать не нужно.

## Задание №3

Требуется посчитать, сколько раз в «Капитанской дочке» встречается слово "Пугачев" без учета частичных совпадений.

## Задание №4

Файл [data/blok.txt](/data/blok.txt) содержит одно из самых известных стихотворений
Александра Блока «Ночь, улица, фонарь, аптека...».

Требуется адаптировать это стихотворение для детей от 0 до 3 лет
(утверждается, что до 5 лет дети не могут понять концепцию смерти):
заменить все вхождения слова "Живи" на "Не спи" и "Умрёшь" на "Уснёшь".
Результат вывести в файл `data/blok_kids_edition.txt`.

> Вам понадобится [sed](https://www.gnu.org/software/sed/manual/sed.html),
> а конкретно формат команды для замены
> [`s/regexp/replacement/flags`](https://www.gnu.org/software/sed/manual/sed.html#The-_0022s_0022-Command).

## Задание №5

Файл [data/students.csv](/data/students.csv) содержит список студентов
и соответствующих номеров студенческих билетов в формате [CSV](https://en.wikipedia.org/wiki/Comma-separated_values):
```
<Фамилия> <Имя>[ <Отчество>],<Номер>
```

> [!NOTE]
> Отчество заключено в квадратные скобки, потому что является опциональным элементом
> (например, у студентов из Казахстана нет отчества в паспорте).

Требуется переформатировать данный список в более человеко-читаемый вид
(и сохранить результат в файл `data/students.txt`):
```
<Имя> <Фамилия> (<Номер>)
```

Например:
```console
$ cat data/students.csv
Иванов Иван Иванович,000020
Назарбаева Хаят,120010
О Евгений Петрович,999999
...
$ bash solution/task2.sh && cat data/students.txt
Иван Иванов (000020)
Хаят Назарбаева (120010)
Евгений О (999999)
...
```

> Вам понадобится [sed](https://www.gnu.org/software/sed/manual/sed.html).
>
> В частности опция `--regexp-extended` (также `-E` или `-r`),
> активирующая режим расширенных регулярных выражений, поддерживающих
> группировку и обратные ссылки.
>
> **Рекомендация**  
> Настоятельно рекомендуется ознакомиться с разделом
> [5.7 Back-references and Subexpressions](https://www.gnu.org/software/sed/manual/sed.html#Back_002dreferences-and-Subexpressions)
> из документации, особенно с *последним примером*:
> ```console
> $ echo "James Bond" | sed -E 's/(.*) (.*)/The name is \2, \1 \2./'
> The name is Bond, James Bond.
> ```
