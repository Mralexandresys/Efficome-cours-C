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

état de le méoire la la ligne 13 :

| adresse mémoire   |  data  | variable|
| ------------ | ------------ | -----------|
|  0xab001 | 42  | a |
|  0xab002 | 100  | b |
| 0xab003 | 0xab001 | pa |
| 0xab004 | 0xab002 | pb |

état de la mémoir a la ligne 15

| adresse mémoire   |  data  | variable|
| ------------ | ------------ | -----------|
|  0xab001 | 42  | a |
|  0xab002 | 100  | b |
| 0xab001 | 42 | pa |
| 0xab002 | 100 | pb |
| 0xab003 | 42 | tmp |

état de la mémoir a la ligne 16 :

| adresse mémoire   |  data  | variable|
| ------------ | ------------ | -----------|
|  0xab001 | 100  | a |
|  0xab002 | 100  | b |
| 0xab003 | 100 | pa |
| 0xab004 | 100 | pb |
| 0xab005 | 42 | tmp |

état de la mémoir a la ligne 17 :

| adresse mémoire   |  data  | variable|
| ------------ | ------------ | -----------|
|  0xab001 | 42  | a |
|  0xab002 | 100  | b |
| 0xab003 | 42 | pa |
| 0xab004 | 100 | pb |
| 0xab005 | 42 | tmp |

	
