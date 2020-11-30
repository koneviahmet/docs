# diziler

``` bash
OS=( 'Linux' 'Windows' 'Unix' )

echo "${OS[@]}" #Tüm dizi elemanlerını gösterir

echo "${OS[2]}"

echo "${!OS[@]}" #Tüm dizinin index sırasını gösterir

echo "${#OS[@]}" #Tüm dizi eleman sayısını gösterir

OS[3]='Mac'

echo "${OS[@]}"

unset OS[1]

echo "${OS[@]}"

echo "${!OS[@]}"

```

