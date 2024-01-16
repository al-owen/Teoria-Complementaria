

Las rutas en Laravel sirven para definir cómo se manejan las solicitudes HTTP entrantes. Al definir rutas, asocias URL con acciones específicas o vistas en tu aplicación. Cada ruta puede apuntar a un controlador y una función específicos o devolver una vista directamente.


Ejemplo de una ruta básica en el archivo `routes/web.php`:
``` php
Route::get('/home', function () {
	return 'Welcome Home!'; 
});
```

Este código especifica que cuando un usuario visite `http://tuapp.com/home`, Laravel devolverá el texto "Welcome Home!". Las rutas son fundamentales para dirigir el tráfico en tu aplicación hacia el contenido o funcionalidad correcta.

Las rutas pueden apuntar a controladores:

``` php
Route::get('/user/{id}', [UserController::class, 'show']);
```

Existen varios tipos de rutas con diferentes metodos:

- `get`: Recuperar recursos (lectura).
``` php
Route::get($uri, $callback);
```
- `post`: Crear un recurso (escritura).
``` php
Route::post($uri, $callback); 
```
- `put`: Actualizar un recurso completamente.
``` php
Route::put($uri, $callback);
```
- `patch`: Actualizar parcialmente un recurso.
``` php
Route::patch($uri, $callback); 
```
- `delete`: Eliminar un recurso.
``` php
Route::delete($uri, $callback); 
```
- `options`: Obtener información sobre las capacidades de comunicación del recurso o servidor.
``` php
Route::options($uri, $callback);
```