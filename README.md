# some bash shells i need

```bash

#!/bin/bash
### Genrating genome fasta file with proper header,like "ch1"

# chromsome array
arr=(1 2 3 4 5 x y)

i=0
zcat $1 | while read line
do
        if [[ ${line:0:1} == \>  ]]
        then
                var=${arr[$i]}
                echo \>ch$var >> ref.fa
                let i++
                #echo $line | cut -f5 -d" " |xargs  echo ">ch" | sed "s/ //g" >> ref.fa
        else
                echo $line >> ref.fa
        fi

done

echo "done"


```
