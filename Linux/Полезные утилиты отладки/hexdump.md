---
tags:
  - linux
  - utility
---
Выводит содержимое файла в 16-, 10-, 8- формате или интерпретирует содержимое как ASCII 

Наиболее частый применяемый ключ: `-C` `--canonical` -- выводих hex+ASCII для просмотра

Пример использования:
```bash
edge-platform$ grep renames platform/Aquarius/T30-S001DC-0.rules | hexdump -C
00000000  23 20 4e 65 74 77 6f 72  6b 20 72 65 6e 61 6d 65  |# Network rename|
00000010  73 20 66 6f 72 20 54 33  30 2d 53 30 30 31 44 d0  |s for T30-S001D.|
00000020  a1 2d 30 0a                                       |.-0.|
00000024
edge-platform$ 
```

