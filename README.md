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
 
 ---------------------------------------------------------------------------------------------------------
 - $pdo-> prepare() : prepare a sql command : prepare($sql_command)
 - $statement-> execute() : prepare method will not work without execute method. when we call prepare method, we have to call execute method after prepare method.
 - $all_rows = statement-> fetchAll() : fetch all rows of a table
 ##### bindParam() and bindValue() : bindParam and bindValue are same, we can use one of them
 
 For a single variable
 ```
    $user_name = 'junaid';
    $sql = "SELECT * FROM login_php WHERE username=:userName";    
    $statement = $pdo->prepare($sql);
    $statement->bindParam(':userName', $user_name, PDO::PARAM_STR);
    $statement->execute();
    $all_rows = $statement->fetchAll(PDO::FETCH_ASSOC);
    
    // we get all values those match the sql condition
 ```
 
 For multiple variable
 ```
     $user_name = 'junaid';
    $user_email = 'test@gmail.com';
    $sql = "SELECT * FROM login_php WHERE username=:userName AND email=:userEmail";    
    $statement = $pdo->prepare($sql);
    $statement->bindParam(':userName', $user_name, PDO::PARAM_STR);
    $statement->bindParam(':userEmail', $user_email, PDO::PARAM_STR);
    $statement->execute();
    $all_rows = $statement->fetchAll(PDO::FETCH_ASSOC);
 ```
 ## pdo crud in secure way
 
 #### read all rows
 ```
    $sql = "SELECT * FROM login_php";
    $statement = $pdo->prepare($sql);
    $statement->execute();
    $all_rows = $statement->fetchAll();

 ```
 
 
 
 
 
 
 
 
 
