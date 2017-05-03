# English

This library is used to extract information from a configuration file, the goal of ant is to produce the smallest software possible for that task.

You can use the following functions:

Get_string -> get the value of a string field and copy it to the specified string, eg: "get_string (config_file," field ", array_destination);", 
If it can not find the field inside the file it returns -666, if it can not open the file -667, if no error occurs it returns 0.

Get_int -> return the value of an int field, 
If it can not find the field inside the file it returns -666, if it can not open the file it returns -667.

## Why -666 and -667 to handle errors? 
Because many values ​​in configuration files are usually -1 or -2, while 
-666 and -667 are less common.

# Español

Esta biblioteca sirve para extraer información de un archivo de configuración, el objetivo de ant es producir el software más pequeño posible para dicha tarea.

Puedes usar las siguientes funciones:

get_string -> obtiene el valor de un campo string y lo copiará al string expecificado, ejemplo: "get_string(archivo_conf, "campo", array_destino);", 
sino puede encontrar el campo dentro del fichero devuelve -666, sino puede abrir el fichero -667, sino se produce ningún error devuelve 0.

get_int -> devuelve el valor de un campo int, 
si no puede encontrar el campo dentro del fichero devuelve -666, si no puede abrir el fichero devuelve -667.

## ¿Por qué -666 y -667 para manejar errores?
Muchos valores en archivos de configuración suelen ser -1 o -2, mientras 
que -666 y -667 son valores menos comunes.

# Example

## In plain text file "test.conf":
```
Field1=foobarstring
Field2=34
#Foobar comment
Field3=foobarstring2
```
## In C file:

```
#include <stdio.h>
#include <stdlib.h>
#include "ant.h"

void main() {
    
    int number;
    char string[15];
    int status=get_string("test.conf", "Field1", string);
    
    if(status==-666) printf("The field not exist\n");
    if(status==-667) printf("The file not exist\n");
    
    number=get_int("test.conf", "Field2");
    
    if(number==-666) printf("The field not exist\n");
    if(number==-667) printf("The file not exist\n");
    
    
    if(status>=-665 && number>=-665) {
        printf("%s\n", string);
        printf("%d\n", number);
    }
    
}
```
## For compile
```
CC myprogram.c ant.c -o myprogram
```
