---
title: 'Font PSF'
---

Il PSF è un vecchio formato di font in formato bitmap. È ancora usato ed è supportato dai pacchetti che gestiscono la console di Linux. Se usate Linux da qualche parte avete sicuramente dei file PSF, magari compressi con gzip.

Il codice qui sotto mostra come decodificare i singoli caratteri (glyph). L'avevo scritto per una [piccola libreria grafica](https://bitbucket.org/venza/libfb).

```c
#include <stdio.h>
#include "FBlib.h"

FILE *gunzip(FILE* fp, char* path)
{
    char command[200];

    fclose(fp);
    sprintf(command, "gunzip -c %s > /tmp/FBfont.psf", path);
    system(command);
    fp = fopen("/tmp/FBfont.psf", "r");
    system("rm /tmp/FBfont.psf");
    return fp;
}

int main(int argc, char *argv[])
{
    FILE *font;
    char byte;
    int filemode;
    char fontheight;
    int i, j, k;

    if (argc > 1) {
        font = fopen(argv[1], "r");
        if (font == NULL) {
            printf("%s was not found", argv[1]);
            return -1;
        }
    } else {
        font = stdin;
    }

    byte = fgetc(font);
    if (byte == 31) {
        byte = fgetc(font);
        if (byte = 139) {
            font = gunzip(font, argv[1]);
            byte = fgetc(font);
        }
    }
        if (byte != 0x36) {
        printf("%s is not a psf font file", argv[1]);
        return -1;
    }

    byte = fgetc(font);
    if (byte != 0x04) {
        printf("%s is not a psf font file", argv[1]);
        return -1;
    }
    filemode = fgetc(font);
    if (filemode == 1 || filemode == 3)
        filemode = 512;
    if (filemode == 0 || filemode == 2)
        filemode = 256;
    fontheight = fgetc(font);
    for (k=0; k &lt; filemode; k++)     {
        for(j=0; j &lt; fontheight; j++) {
            byte = fgetc(font);
            for(i=128; i>0; i/=2) {
                if(byte & i)
                    printf("O");
                else
                    printf(" ");
            }
            printf("\n");
        }
    printf("\n");
    }

    fclose(font);
    return 0;
}
```
