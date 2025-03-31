```C
#include <stdio.h>
#include <fcntl.h>
#include <stdlib.h>
main()
{
 int a,ilosc;
 int plik1;
 char wyraz[21];
 a=99;
 printf("program 1 \n a=%d\n",a);
 plik1=creat("dane.txt",0666);
 ilosc=write(plik1,"To jest tekst AAA.\n",20);
 printf("Zapisano %d znakow\n",ilosc);
 close(plik1);
 plik1=open("dane.txt",O_RDWR,0);
 if (plik1==-1) printf("Blad otwarcia do odczytu\n");
 ilosc=write(plik1,"A oto o kocie Ali.\n",20);
 printf("Zapisano %d znakow\n",ilosc);
 ilosc=write(plik1,"I o innych kotach.\n",20);
 printf("Zapisano %d znakow\n",ilosc);
 lseek(plik1,0L,0);
 /* lseek - trzeci arg. - odmierzanie wartosci drugiego  od
 0 - poczatku, 1 -biezacej poz. wskaznika, 2-konca pliku*/
 do
 {
  ilosc=read(plik1,wyraz,20);
  printf("Odczytano %d znakow\n", ilosc);
  printf("Odczytane: %s\n",wyraz);
 }while(ilosc!=0);
 lseek(plik1,-20L,2); 
 ilosc=read(plik1,wyraz,20);
 printf("Ostatni Odczyt - po lseek: %d znakow\n", ilosc);
 printf("Odczytane: %s\n",wyraz); 
 close(plik1);
 printf("Aby zakonczyc Wpisz liczbe:");
 scanf("%d",&a);
}
```
