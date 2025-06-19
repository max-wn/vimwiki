## sdcv

is a command line dictionary. It provides access to dictionaries in StarDict's
format.

### links

1. https://wiki.archlinux.org/title/Sdcv
2. https://formulae.brew.sh/formula/sdcv#default
3. https://dushistov.github.io/sdcv/
4. https://github.com/Dushistov/sdcv

#### dictionaries database

1. https://web.archive.org/web/20200702000038/http://download.huzheng.org/

#### Adding dictionaries

Once you have the appropriate files you can extract them into
`/usr/share/stardict/dic`. If you do not have root permission, you can set the
`STARDICT_DATA_DIR` environment variable. For example: `export STARDICT_DATA_DIR=$XDG_DATA_HOME` sdcv will look in the dic subdirectory so
make sure that it is created and then place your dictionary files inside it.
If all is done correctly, sdcv should be able to output definitions for words
passed into it.

### Использование:

  `sdcv [ПАРАМЕТР…] слова`

```
Параметры справки:
  -h, --help                            Показать параметры справки

Параметры приложения:
  -v, --version                         показать номер версии и завершить работу
  -l, --list-dicts                      показать список доступных словарей и завершить работу
  -u, --use-dict=имя_словаря            для поиска использовать только этот словарь с таким именем
  -n, --non-interactive                 для использования в скриптах
  -j, --json-output                     выдать результат в JSON формате
  --json                                выдать результат в JSON формате
  -e, --exact-search                    не использовать нечеткий поиск похожих слов, вернуть только точные совпадения
  -0, --utf8-output                     вывод программы должен быть в utf8
  -1, --utf8-input                      ввод программы в utf8
  -2, --data-dir=путь/до/директории     использовать эту директорию в качестве пути к "stardict data" директории
  -x, --only-data-dir                   использовать словари только из data-dir, не искать в пользовательских и системных каталогах
  -c, --color                           раскрашивать вывод в разные цвета
```

---

[[/index|Get Back To Index]]
