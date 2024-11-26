### Variables:

``` php
{$nombre}
```
Si en PHP asignas `$smarty->assign('nombre', 'Joan');`, en la plantilla `{$nombre}` imprimirá `Joan`.

### Objetos:
Se pueden llamar a los parámetros de los objetos de la misma manera que en php
``` php
{$persona->nombre}
```
### Condicionales (if/else/elseif):

``` php
{if $calificacion >= 90} 
	<p>¡Excelente! Tu calificación es {$calificacion}, estás en el rango A.</p> 
{elseif $calificacion >= 80} 
	<p>¡Muy bien! Tu calificación es {$calificacion}, estás en el rango B.</p> 
{elseif $calificacion >= 70} 
	<p>¡Bien hecho! Tu calificación es {$calificacion}, estás en el rango C.</p> 
{else}
	<p>Necesitas mejorar. Tu calificación es {$calificacion}, estás por debajo del rango aceptable.</p> 
{/if}
```

### Bucle foreach:
```php
{foreach from=$usuarios item=usuario}
    Nombre: {$usuario.nombre}, Edad: {$usuario.edad}
{/foreach}
```
Si `$smarty->assign('usuarios', [['nombre' => 'Juan', 'edad' => 25], ['nombre' => 'Ana', 'edad' => 22]]);`, mostrará los datos de cada usuario.

### Ciclo for:
```php
{for $i=1 to 5}
    Número: {$i}
{/for}
```

### Include:
```php
{include file='header.tpl'}
```

### Set (asignación):
Asigna un valor a una variable
```php
{assign var="saludo" value="Hola Mundo"}
{$saludo}
```

### Function:
Llama a funciones personalizadas.
```php
{my_function param="valor"}
```
### Strip:
Elimina espacios y saltos de línea innecesarios.
```php
{strip}
    <p>Texto con espacios y saltos</p>
{/strip}
```

