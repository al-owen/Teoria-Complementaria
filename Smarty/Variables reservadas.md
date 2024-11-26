### $smarty.const:

Accede a constantes de PHP en las plantillas.
```php
{$smarty.const.PHP_VERSION}
```
### $smarty.now
Devuelve la marca de tiempo actual (timestamp).
```php
{$smarty.now|date_format:"%Y-%m-%d"}
```
Esto imprime la fecha actual en formato `YYYY-MM-DD`.

### $smarty.version
Muestra la versión de Smarty en uso.
```php
<p>Smarty versión: {$smarty.version}</p>
```

### $smarty.get
Accede a variables `$_GET` de PHP.
```php
<p>ID recibido por GET: {$smarty.get.id}</p>
```

### $smarty.post
Accede a variables `$_POST` de PHP.
```php
<p>Nombre recibido por POST: {$smarty.post.nombre}</p>
```

### $smarty.session
Accede a variables de sesión `$_SESSION`.
```php
<p>Usuario en sesión: {$smarty.session.usuario}</p>
```

### $smarty.request
Accede a variables de `$_REQUEST`.
```php
<p>Token recibido: {$smarty.request.token}</p>
```