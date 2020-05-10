#Bioinformatics scripts bash and python
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


```bash
#~/usr/bin/python3
### Filter sam data with proper tag,for details, go to
import sys
def filter_sam(f,o):
        with open(f,"r") as f:
                with open(o,"w") as o:
                        for line in f:
                                #print(line)
                                if line.startswith("@"):
                                        o.write(line)
                                else:
                                        l = line.split()
                                        if int(l[1]) in [83,99,147,163]:
                                                o.write(line)


filter_sam(sys.argv[1],sys.argv[2])


```
