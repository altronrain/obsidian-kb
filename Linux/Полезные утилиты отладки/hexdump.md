---
tags:
  - linux
  - utility
---

Выводит содержимое файла в 16-, 10-, 8- формате или интерпретирует содержимое как ASCII 

Наиболее частый применяемый ключ: `-C` `--canonical` -- выводих hex+ASCII для просмотра

## tldr

```tldr
 An ASCII, decimal, hexadecimal, octal dump.  
 See also: `hexyl`, `od`, `xxd`.  
 More information: <https://manned.org/hexdump>.  
  
 Print the hexadecimal representation of a file, replacing duplicate lines by '*':  
  
     hexdump path/to/file  
  
 Display the input offset in hexadecimal and its ASCII representation in two columns:  
  
     hexdump [-C|--canonical] path/to/file  
  
 Display the hexadecimal representation of a file, but interpret only n bytes of the input:  
  
     hexdump [-C|--canonical] [-n|--length] number_of_bytes path/to/file  
  
 Don't replace duplicate lines with '*':  
  
     hexdump [-v|--no-squeezing] path/to/file
```

## Примеры из практики

1. Вывод содержимого файла (тут символ оказался не ASCII в чем и была проблема)
```bash
edge-platform$ grep renames platform/Aquarius/T30-S001DC-0.rules | hexdump -C
00000000  23 20 4e 65 74 77 6f 72  6b 20 72 65 6e 61 6d 65  |# Network rename|
00000010  73 20 66 6f 72 20 54 33  30 2d 53 30 30 31 44 d0  |s for T30-S001D.|
00000020  a1 2d 30 0a                                       |.-0.|
00000024
edge-platform$ 
```
тут символ C в тексте T30-S001DC-0 оказался не ASCII а в русской раскладке, в чем и была проблема. Hexdump тут помог