# while loops

```  bash
#! /bin/bash

i=1

while (($i<=2)) 
do
    echo $i
    ((i++))
    sleep 1
    gnome-terminal
done   

```



# for loops

```bash
#! /bin/bash

for (( i=0;i<=5;i++ ))
do
  echo $i
done  
--------
for i in ls pwd
do
  echo "----------$i-----------"
  $i
  echo
done 
--------
#! /bin/bash

for i in {1..10}
do
echo $i
done  
---------
#! /bin/bash

for i in {1..10..2}
do
echo $i
done

```

# break, contuniu, until

```bash
#! /bin/bash

for ((i=0;i<=10;i++))
do
    if[ $i -gt 5 ]
    then
    break
    fi
    echo "$i"
done
----------------------------------
#! /bin/bash

for ((i=0;i<=10;i++))
do
    if [ $i -eq  2 -o $i -eq 6 ]
    then
    continue
    fi
    echo "$i"
done
------------------------------
#! /bin/bash

i=1

until (($i >= 10))
do
  echo $i
  ((i++)) # i=$((i+1))
done

```

