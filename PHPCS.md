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
