
>[!question]-  Answer
> [Разбор](https://kinescope.io/n7sBzznEhivQymgzVGwfhY)
> ```go
> package main
> 
> func isIsomorphic(s string, t string) bool {
>     // sMap: ключ - символ из строки s,
>     //  значение - соответствие с символом из строки t
>     // tMap: ключ - символ из строки t,
>     //  значение - соответствие с символом из строки s
>     sMap := make(map[byte]byte)
>     tMap := make(map[byte]byte)
>     
>     for i := 0; i < len(s); i++ {
>         // если текущий символ s[i] уже встречался раньше, то
>         //  проверяем, что он соответствует тому же символу из
>         //  строки t, что и в прошлый раз
>         if val, ok := sMap[s[i]]; ok && val != t[i] {
>             return false
>         }
>         // аналогичная проверка для строки t необходима, чтобы учесть условие,
>         //  что ни один символ не может соответствовать 2-ум разным (даже для строки t)
>         if val, ok := tMap[t[i]]; ok && val != s[i] {
>             return false
>         }
>         // запоминаем, сопоставление символов для строк s и t
>         sMap[s[i]] = t[i]
>         tMap[t[i]] = s[i]
>     }
>     
>     return true
> }
> ```




