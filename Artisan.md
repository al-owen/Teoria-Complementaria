
- [[#Serve:|Serve:]]
- [[#List:|List:]]
- [[#Migrate:|Migrate:]]
- [[#Make:|Make:]]
	- [[#Make:#make:controller|make:controller]]
	- [[#Make:#make:middleware|make:middleware]]
	- [[#Make:#make:migration|make:migration]]
	- [[#Make:#make:model|make:model]]
	- [[#Make:#make:resource|make:resource]]
	- [[#Make:#make:view|make:view]]

## Serve: 
Inicia el servidor de desarrollo.
``` bash
php artisan serve
```
## List: 
Muestra todos los comandos disponibles.
``` bash
php artisan list
```
## Migrate: 
Ejecuta las migraciones de base de datos.
``` bash
php artisan migrate
```
## Make: 
Permite crear diferentes componentes 
### make:controller
Crea una nueva clase de controlador
``` bash
php artisan make:controller [Nombre]
```
### make:middleware
Crea un middleware
``` bash
php artisan make:middleware [Nombre]
```
### make:migration
Crea un nuevo fichero de migración para generar la base de datos 
``` bash
php artisan make:migration [Nombre]
```
### make:model
Crea un nuevo modelo 
``` bash
php artisan make:model [Nombre]
```
### make:resource
Crea un nuevo recurso
``` bash
php artisan make:resource [Nombre]
```
### make:view
Crea una nueva vista
``` bash
php artisan make:view [Nombre]
```