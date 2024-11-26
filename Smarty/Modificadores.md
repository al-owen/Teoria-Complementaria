### capitalize
Convierte el primer carácter de la cadena a mayúscula.
```php
{$nombre|capitalize}
```
Si {$nombre} es "joan", el resultado será "Joan".

### upper
Convierte la cadena a mayúsculas.
```php
{$texto|upper}
```
Si {$texto} es "hola", el resultado será "HOLA".

### lower
Convierte la cadena a minúsculas.
```php
{$texto|lower}
```
Si {$texto} es "HOLA", el resultado será "hola".

### truncate
Trunca una cadena a una longitud específica.
```php
{$descripcion|truncate:20}
```
Si {$descripcion} es "Este es un texto largo que necesita ser truncado.", el resultado será "Este es un texto...".

### date_format
Formatea una fecha usando patrones de formato.
```php
{$smarty.now|date_format:"%Y-%m-%d"}
```
Si {$smarty.now} representa la fecha actual, el resultado podría ser "2024-11-26".

### default
Devuelve un valor por defecto si la variable está vacía.
```php
{$usuario|default:"Invitado"}
```
Si {$usuario} no tiene valor, mostrará "Invitado".

### replace
Reemplaza partes de una cadena con otra.
```php
{$texto|replace:"mundo":"amigos"}
```
Si {$texto} es "Hola mundo", el resultado será "Hola amigos".

### count_characters
Cuenta el número de caracteres en una cadena.
```php
{$texto|count_characters}
```
Si {$texto} es "Hola", el resultado será 4.

### count_words
Cuenta el número de palabras en una cadena.
```php
{$texto|count_words}
```
Si {$texto} es "Hola mundo", el resultado será 2.

### strip
Elimina espacios en blanco, saltos de línea y tabulaciones.
```php
{$texto|strip}
```
Si {$texto} es " Hola mundo ", el resultado será "Hola mundo".

### count
Devuelve el número de elementos en un array.
```php
{$usuarios|count}
```
Si {$usuarios} tiene 3 elementos, el resultado será 3.

