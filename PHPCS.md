# database_column_fetch

fetch database column using php and query

```
    function getTableColumn($tableName)
    {
        $check_db = $this->db()->pdo()->query("SELECT COLUMN_NAME, COLUMN_TYPE
        FROM INFORMATION_SCHEMA.COLUMNS
        WHERE TABLE_SCHEMA = 'sik9'
        AND TABLE_NAME = '".$tableName."';");
        $check_db->execute();
        $result = $check_db->fetchAll();
        return $result;
    }
```

# controller_fetch_column_db

controller untuk return column database dari model

```
public function postTableColumn(){
      $_POST['table'];
      echo json_encode($this->convertToJavascriptArray($this->core->getTableColumn($_POST['table'])));
      exit();
    }
```

# query_wraper_crud

## create_data

## read_data
cara read data dari database

    //read simple query wrapper return multi data array    
    $data = $this->core->mysql('nama_table')->where('nama_column',$_POST['data_dikirim'])->toArray();
    
    //read simple query wrapper return single array
    $data = $this->core->mysql('nama_table')->where('nama_column',$_POST['data_dikirim'])->oneArray();
    
    //read simple query wrapper return json parse data
    $data = $this->core->mysql('nama_table')->where('nama_column',$_POST['data_dikirim'])->toJson();

cara read data dari database menggunakan sql raw
        $sql =  "statemen sql query disini";
        $stmt = $this->core->mysql()->pdo()->prepare($sql);
        $stmt->execute();
        $rows = $stmt->fetchAll();
        

## edit_data

## delete_data

