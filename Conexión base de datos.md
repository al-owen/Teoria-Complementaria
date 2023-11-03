## Conexión

Para conectarse a una base de datos en PHP, generalmente se utiliza la extensión `mysqli` para bases de datos MySQL o la extensión `PDO` para múltiples tipos de bases de datos. Aquí se muestra un ejemplo de conexión con MySQL utilizando `mysqli`.

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "database";

// Crear conexión
$conn = new mysqli($servername, $username, $password, $dbname);

// Verificar conexión
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Cerrar conexión
$conn->close();
?>
```

## Select

Las consultas SQL en PHP utilizando la extensión `mysqli` se pueden realizar de varias maneras, pero las más comunes son el método `query` para consultas simples y el método `prepare` para consultas preparadas. Aquí hay ejemplos para cada uno:

### Query
```php
// Suponemos que $conn es la conexión a la base de datos existente

// Esta línea establece la consulta SQL que deseas ejecutar.
$sql = "SELECT id, name FROM table_name";

// Aquí ejecutas la consulta en la base de datos representada por la conexión `$conn` y almacenas el resultado en `$result`.
$result = $conn->query($sql); 

// Luego, verificas si el resultado tiene filas. `num_rows` es una propiedad de la clase `mysqli_result` que indica el número de filas obtenidas.
if ($result->num_rows > 0) {
    // `fetch_assoc` recupera cada fila como un array asociativo. La clave del array es el nombre de la columna y el valor es el dato correspondiente de la fila.
    while ($row = $result->fetch_assoc()) {
        echo "ID: " . $row["id"] . " - Name: " . $row["name"] . "<br>";
    }
} else {
    // Si no hay filas, entonces imprimes "0 results", indicando que no se encontraron resultados para la consulta.
    echo "0 results";
}

```

### Consulta preparada
```php
// Suponemos que $conn es la conexión a la base de datos existente

// Establece la consulta SQL con un placeholder para el valor de 'id'.
$sql = "SELECT id, name FROM table_name WHERE id = ?";

// Prepara la consulta SQL para su ejecución y devuelve un objeto de declaración preparada.
$stmt = $conn->prepare($sql);

// Aquí asignas un valor específico al 'id' que deseas buscar en la base de datos.
$id = 1;

// 'bind_param' vincula las variables a los parámetros del marcador de posición '?' de la declaración SQL.
// El "i" indica que la variable correspondiente es de tipo entero.
$stmt->bind_param("i", $id);

// Ejecuta la declaración preparada.
$stmt->execute();

// 'bind_result' vincula las columnas del conjunto de resultados a las variables PHP.
// Aquí, $id y $name son las variables donde se almacenarán los datos de las columnas 'id' y 'name'.
$stmt->bind_result($id, $name);

// El bucle 'while' itera a través del conjunto de resultados y cada llamada a 'fetch' obtiene los resultados de la siguiente fila.
while ($stmt->fetch()) {
    // Imprime los valores de las variables que han sido vinculadas a las columnas del resultado.
    echo "ID: " . $id . " - Name: " . $name . "<br>";
}

$stmt->close();
```

## Insert

Para realizar una inserción preparada en PHP usando MySQLi, sigue estos pasos:

1. Preparar la sentencia SQL con placeholders para los valores que quieras insertar.
2. Preparar la sentencia con `prepare()`.
3. Vincular los parámetros a los placeholders con `bind_param()`.
4. Ejecutar la sentencia preparada con `execute()`.

Aquí hay un ejemplo de cómo se haría:

```php
// Suponemos que $conn es la conexión a la base de datos existente

// 1. La sentencia SQL con placeholders
$sql = "INSERT INTO table_name (column1, column2) VALUES (?, ?)";

// 2. Preparar la sentencia
$stmt = $conn->prepare($sql);

if ($stmt === false) {
    die("Error al preparar la consulta: " . $conn->error);
}

// 3. Vincular los parámetros (asumiendo que column1 es un entero y column2 es un string)
$column1Value = 123;
$column2Value = 'Un valor de texto';

// 'is' en bind_param indica que el primer parámetro es un entero (i) y el segundo es un string (s)
$stmt->bind_param("is", $column1Value, $column2Value);

// 4. Ejecutar la sentencia
if ($stmt->execute()) {
    echo "Registro insertado con éxito.";
} else {
    echo "Error al insertar registro: " . $stmt->error;
}

// Cerrar la sentencia preparada
$stmt->close();
```

### Delete 

Para eliminar un registro de una base de datos en PHP utilizando MySQLi y consultas preparadas, sigue estos pasos:

1. Escribir la sentencia SQL para eliminar, con placeholders para los criterios de eliminación.
2. Preparar la sentencia con `prepare()`.
3. Vincular los parámetros a los placeholders con `bind_param()`.
4. Ejecutar la sentencia preparada con `execute()`.

A continuación se muestra un ejemplo de cómo eliminar un registro basado en un ID único:

```php
// Suponemos que $conn es la conexión a la base de datos existente

// 1. La sentencia SQL con placeholders
$sql = "DELETE FROM table_name WHERE id = ?";

// 2. Preparar la sentencia
$stmt = $conn->prepare($sql);

if ($stmt === false) {
    die("Error al preparar la consulta: " . $conn->error);
}

// 3. Vincular los parámetros (asumiendo que el id es un entero)
$idToDelete = 10;
$stmt->bind_param("i", $idToDelete);

// 4. Ejecutar la sentencia
if ($stmt->execute()) {
    echo "Registro eliminado con éxito.";
} else {
    echo "Error al eliminar registro: " . $stmt->error;
}

// Cerrar la sentencia preparada
$stmt->close();
```