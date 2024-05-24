# DB connect

```php

$servername = "mysql";
$dbname = "my-db";
$username = "root";
$password = "root";
$charset = "utf8";

$option = [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
    PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC
];


$dsn = "mysql:host=$servername;dbname=$dbname;charset=$charset";

$connect = new PDO($dsn, $username, $password, $option);

```
