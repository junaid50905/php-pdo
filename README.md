# php-pdo

### create
  ```javascript
  $sql = "";
  $statement = $pdo->prepare($sql);
  $statement->execute();
  ```
  
  
### read
  
  
  
  $sql = "";
  $statement = $pdo->query($sql);
  $allrows = $statement->fetchAll(PDO::FETCH_ASSOC); // through loop(we use foreach) we will get the single row
 
