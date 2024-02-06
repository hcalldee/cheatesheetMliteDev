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
cara save data menggunakan query builder

    //$_POST berisi data yang ingin disimpan
    /*
    struktur nya seperti berikut 
    
    array(
    'Column'=>'Value yang dirubah',
    ...
    )
    
    dalam bentuk JSON di client
    
    let data = {
        key:"value",
        ...
    }
    
    */

    //fungsi pada controller
    // cek data terlebih dahulu apakah sudah ada ?
    if(!$this->core->mysql('tabel')->where('nama_column_pivot',$pivot)->oneArray()){
        // jika tidak ada
        $this->core->mysql('tabel')->save($_POST);
        echo json_encode('data disimpan');
    }else{
        // jika sudah ada
        echo json_encode('data duplikat');
    }
    

## read_data
cara read data dari database menggunakan query builder

    //read simple query wrapper return multi data array    
    $data = $this->core->mysql('nama_table')->where('nama_column',$_POST['data_dikirim'])->toArray();
    
    //read simple query wrapper return single array
    $data = $this->core->mysql('nama_table')->where('nama_column',$_POST['data_dikirim'])->oneArray();
    
    //read simple query wrapper return json parse data
    $data = $this->core->mysql('nama_table')->where('nama_column',$_POST['data_dikirim'])->toJson();

cara read data dari database menggunakan sql raw

    $sql = "statemen sql query disini";
    $stmt = $this->core->mysql()->pdo()->prepare($sql);
    $stmt->execute();
    $rows = $stmt->fetchAll();
        

## edit_data
cara edit data menggunakan query builder

    //$_POST berisi data yang ingin diubah
    /*
    struktur nya seperti berikut 
    
    array(
    'Column'=>'Value yang dirubah',
    ...
    )
    
    dalam bentuk JSON di client
    
    let data = {
        key:"value",
        ...
    }
    
    */

    //fungsi pada controller
    $this->core->mysql('tabel')->where('nama_column_pivot',$pivot)->update($_POST);

## delete_data

