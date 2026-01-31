# Исбользование библиотечных функций без SASM

## Для чего конктретно это нужно
Эта фигня нужна для того чтобы ипользовать фунцкии `io_print_dec`, `io_get_dec` итд без SASM, допустим в вашем любимом редакторе (VSCode?)

> Консольные комадны теперь без занака доллар ($) => теперь можно копировать всю строку

## Шаг 0

Заходим на виртуалку 

## Загрузка пакетов
Прежде всего нужно установить необходимые пакеты. Потребуется ввести пароль

**Попросит ввести `Y` (yes) и нажать `Enter`**
```
sudo apt install git gcc-multilib
```

## Установочка

Заходим в папку
```
cd /usr/local/lib
```

Клонируем рпепозиторий (может потребовать пароль)
```
sudo git clone https://github.com/foured/build_asm.git
```

Создаем 'ссылку' (симлинк) на скрипт (может потребовать пароль)
```
sudo ln -s /usr/local/lib/build_asm/build_asm.sh /usr/local/bin/build_asm
```

## Проверка

Создаем файлик `main.asm` **НЕ В ЭТОЙ ПАПКЕ**

Вставляем в него тестовый код:

```
section .text
extern io_print_dec, io_newline
global main
main:
    mov ebp, esp

    mov eax, 258
    call io_print_dec
    call io_newline

    xor eax, eax
    ret
```

Билдим
```
build_asm main.asm
```

Заупускаем
```
./main.out
```

Должно получиться ``258``
