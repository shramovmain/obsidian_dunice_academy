### Система каталогов Linux
![[rCKD7kPpm4s.jpg]]
### Перемещение между каталогами

```bash
// В каком мы сейча каталоге
pwd

// Переход в домашний каталог 
cd
cd ~
cd /home/user

// Переход в любой другой каталог (если в желаемый каталог можно попасть из текущего)
cd /anyCatalog

//Переход в любой другой каталог (если в желаемый каталог нельзя попасть из текущего)
cd /home/user/anyCatalog_1/anyCatalog_2

Переход на 1 или 2 уровня выше (кол-во уровней не ограничено)
cd ../
cd ../../

Ps: каждый каталог содержит скрытые файлы 
. (указатель на текущий каталог)
.. (указатель на предыдущий каталог)
Да-да, названия состоят из точек!
```
### Работа с файлами и каталогами

```bash
// Создание файла

nano filename // через реадктоор
vim filename // через реадктоор
> filename
touch filename
echo "Content" >> filename // если файла с таким имененм нет, создает его с содержимым "Content", в противном случае, дозаписывает содержимое на новой строке
echo "Content" > filename // если файла с таким имененм нет, создает его с содержимым "Content", в противном случае, перезаписывает содержимое
cat > filename // Создаёт файл с указанным именем и содержимым, введенным из терминала

// Создание ссылок

ln -s target_file link_name // символьная ссылка
ln target_file link_name // жёсткая ссылка

Ограничения для жёстких ссылок: 
- Нельзя ссылаться на директорию
- Нельзя создавать ссылку с одного диска на другой

// Преемещение файла

mv filename /path/to/new/directory

// Переименование файла

mv old_filename new_filename

// Кто сказал, что нельзя переместить и переимновать файл одновременно?

mv old_filename /path/to/new/directory/new_filename

// Удаление файла

rm filename
rm ~/filename // в домашнем каталоге
rm /home/user/Documents/directoryName // в любом другом каталоге (с использованием полного пути)
rm -r ./dirName/*.png // всех файлов с расширением .png в каталоге dirName

// Создания каталога

mkdir directoryName
mkdir ~/directoryName // в домашнем каталоге
mkdir /home/user/Documents/directoryName // в любом другом каталоге (с использованием полного пути)
mkdir -p any/new/directories/directoryName // вместе с созданием каталога, создаёт вложенные дикктерии (any, new, directories)

// Просмотр содержимого каталога

ls
ls -a // в том числе скрытых файлов

// Любые работы с корневым каталогом и его файлами требудет права супер-пользователя

sudo
```

### Права доступа
![[43edf9b00b815dda9101169d0701207b.png]]
В Linux, права доступа к файлам и каталогам управляются с помощью системы разрешений, которая обеспечивает безопасность и управление доступом к ресурсам. Права доступа делятся на три категории: владелец (owner), группа (group) и другие (others).

**Типы прав доступа**
1. **Чтение (r)**: Позволяет пользователю или группе просматривать содержимое файла или каталога.
2. **Запись (w)**: Позволяет пользователю или группе изменять содержимое файла или каталога.
3. **Выполнение (x)**: Позволяет пользователю или группе запускать файл как программу или просматривать содержимое каталога.

**Чтение прав доступа**
Права доступа отображаются в виде строки из девяти символов, разделенных на три группы по три символа. Каждая группа соответствует правам для владельца, группы и других пользователей соответственно.
#### rwx r-x r--

`rwx` - права для владельца (чтение, запись, выполнение).
`r-x` - права для группы (чтение, выполнение).
`r--` - права для других пользователей (чтение).

**Numeric Notations**
Права доступа также могут быть заданы с помощью числовых обозначений, где каждый символ заменяется числом:

`0` - нет прав.
`1` - право на выполнение.
`2` - право на запись.
`4` - право на чтение.

Например, `chmod 755 filename` задает права на чтение, запись и выполнение для владельца, право на чтение и выполнение для группы и право на чтение для других пользователей.

==ЭТО ВАЖНО!==
- Права доступа могут быть изменены только владельцем файла или суперпользователем.
- Права доступа к каталогам влияют на доступ к файлам внутри них.
- Права доступа к файлам и каталогам могут быть изменены рекурсивно с помощью опции `-R` в командах `chmod`, `chown`, и `chgrp`.

```bash
// Просмотр прав доступа в текущем каталоге

ls -l

// Управление правами доступа

chmod +rwx filename // добавляет права на чтение, запись и выполнение для файла
chmod -rwx filename // удаляет права на чтение, запись и выполнение для файла
chmod 777 filename // задает права на чтение, запись и выполнение для всех пользователей
```


### Работа с процессами
Чтобы посмотреть список процессов, если известна часть имени процесса, можно использовать команду `ps` с опцией `grep`. 
Например, если необходимо найти процессы, содержащие в имени слово "chrome", нужно выполнить команду:
```bash
ps // вывод всех процессов в текущем терминале

ps aux // вывод всех процессов

ps aux | grep chrome // поиск всех процессов, содержащих в имени chrome

ps aux | grep PID // поиск всех процессов c таким PID
```
Команда `ps aux` выводит список всех процессов, а `grep chrome` фильтрует вывод, оставляя только строки, содержащие слово "chrome".

Чтобы остановить процессы по PID, можно использовать команду `kill`. 
**Корректная остановка**:
```bash
kill -15 PID
```
**Принудительная остановка**:
```bash
kill -9 PID
```

---
**Полезные ссылки:**

