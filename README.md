# php-pdo(PHP Data Object)

## pdo configaration

  ```
  $host     = 'localhost';
  $database = 'login_registration_system';
  $user     = 'root';
  $password = '';
  $dsn      = "mysql:host=$host;dbname=$db;charset=UTF8";

  try {
      $pdo = new PDO($dsn, $user, $password);

      if ($pdo) {
          return $pdo;
      }
  }catch (PDOException $e) {
      echo $e->getMessage();
  }
  ```

```

$statement = $pdo->prepare($sql) // prepare a sql command for query
$statement = $pdo->query($sql)  // it works same as prepare. But it is less secure than prepare() method
$allrows   = $statement->fetchAll(PDO::FETCH_ASSOC) // fetch all rows of a table 

```
## pdo CRUD

### create

  ```
  $sql = "";
  $statement = $pdo->prepare($sql);
  $statement->execute();
  ```
  
### read
  
  ```
  $sql = "";
  $statement = $pdo->query($sql);
  $allrows = $statement->fetchAll(PDO::FETCH_ASSOC); // through loop(we use foreach) we will get the single row
 ```
