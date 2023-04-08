# php-pdo

## pdo configaration

  ```
  $host = 'localhost';
  $db = 'login_registration_system';
  $user = 'root';
  $password = '';
  $dsn = "mysql:host=$host;dbname=$db;charset=UTF8";

  try {
      $pdo = new PDO($dsn, $user, $password);

      if ($pdo) {
          return $pdo;
      }
  }catch (PDOException $e) {
      echo $e->getMessage();
  }
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
