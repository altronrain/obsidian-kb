---
tags:
  - linux
  - utility
---
- [[#tldr|tldr]]
- [[#Примеры из практики|Примеры из практики]]

Выводит вызовы к библиотекам в процессе работы для указанного процесса

## tldr

```tldr
 Display dynamic library calls of a process.  
 More information: <https://manned.org/ltrace>.  
  
 Print (trace) library calls of a program binary:  
  
     ltrace ./program  
  
 Count library calls. Print a handy summary at the bottom:  
  
     ltrace -c path/to/program  
  
 Trace calls to malloc and free, omit those done by libc:  
  
     ltrace -e malloc+free-@libc.so* path/to/program  
  
 Write to file instead of terminal:  
  
     ltrace [-o|--output] file path/to/program
```

## Примеры из практики

1. Выводим все вызовы к библиотекам `libssl` или `libcrypto` при выполнении бинаря `numa-ssh`
```
ltrace -e "*SSL*" -e "*CRYPTO*" numa-ssh -vvv -o HostKeyAlgorithms=ssh-gost2012-256-cpa admin@192.168.122.161 > lib_calls.txt
```
