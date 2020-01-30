# Cours sur le C et les pointeurs

## Switch des donnés de variable

``` C
#include <stdio.h>
#include <string.h>
#include <stdlib.h>


int main( int ac, char **av){

     int a = 42 , b = 100 ;
	 
     printf("a : %d , b : %d \n", a , b);
    
     int *pa = &a;
     int *pb = &b;

     int tmp = *pa;
     *pa = *pb;
     *pb = tmp;

     printf("a : %d , b : %d\n", a , b);
	 
	 return 0;
}

```
-----

#### résulta : 
```
    a : 42 , b 100
    a : 100 , b 42
```

#### explication

__état de le méoire la la ligne 13 :__

on a mit dans les pointeurs \*pa et \*pb les adresse de a et b


| adresse mémoire   |  data / adresse cible  | variable|
| ------------ | ------------ | -----------|
|  0xab001 | 42  | a |
|  0xab002 | 100  | b |
| 0xab003 | 0xab001 | \*pa |
| 0xab004 | 0xab002 | \*pb |



__état de la mémoir a la ligne 15 :__

on a mit dans la varaible tmp la valeur du pointeur \*pa

| adresse mémoire   |  data / adresse cible  | variable|
| ------------ | ------------ | -----------|
|  0xab001 | 42  | a |
|  0xab002 | 100  | b |
| 0xab003 | 0xab001 | \*pa |
| 0xab004 | 0xab002 | \*pb |
| 0xab005 | 42 | tmp |

__état de la mémoir a la ligne 16 :__

on a mit la valeur du pointeur \*pb dans l'adresse du pointeur \*pa

| adresse mémoire   |  data / adresse cible  | variable|
| ------------ | ------------ | -----------|
|  0xab001 | 100  | a |
|  0xab002 | 100  | b |
| 0xab003 | 0xab001 | \*pa |
| 0xab004 | 0xab002 | \*pb |
| 0xab005 | 42 | tmp |

__état de la mémoir a la ligne 17 :__

| adresse mémoire   |  data / adresse cible  | variable|
| ------------ | ------------ | -----------|
|  0xab001 | 42  | a |
|  0xab002 | 100  | b |
| 0xab005 | 0xab001 | \*pa |
| 0xab002 | 0xab002 | \*pb |
| 0xab005 | 42 | tmp |
