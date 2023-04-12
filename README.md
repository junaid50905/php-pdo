# php-pdo(PHP Data Object)

## pdo configaration

  ```
  $host     = 'localhost';
  $database = 'login_registration_system';
  $user     = 'root';
  $password = '';
  $dsn      = "mysql:host=$host;dbname=$database;charset=UTF8";

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

$statement = $pdo->prepare($sql) // prepare a sql command for query. prepare() method will not work without execute() method

$statement = $pdo->query($sql)  // it works same as prepare. But it is less secure than prepare() method. It will work without execute()

$allrows   = $statement->fetchAll(PDO::FETCH_ASSOC) // fetch all rows of a table FETCH_BOTH=fetch associative and indexed array both, FETCH_ASSOC= fetch associative array, FETCH_NUM= fetch indexed array, 

$statemeent->rowcount() // to get number of rows affected by Query

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
 
 
 // Here is an another way to fetch all rows of a table
 
 // this is the best way to fetch
 ```
  $fetch_all_rows_sql = "SELECT * FROM employees";
  $statement = $pdo->prepare($fetch_all_rows_sql);
  $statement->execute();
  $all_rows = $statement->fetchAll(PDO::FETCH_ASSOC);  
 
 ```
 
 
 
 
 
 
 
 
