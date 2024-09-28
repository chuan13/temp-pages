# Foreign Key 的資訊與修改
<br>

## 找出所有參考此資料表的 Foreign Key
```SQL
SELECT 
    fk.name AS 'ForeignKey 名稱',
    tr.name AS '被參考 資料表',
    cr.name AS '被參考 欄位',
    tp.name AS 'FK 參考 資料表',
    cp.name AS 'FK 參考 欄位'    
FROM 
    sys.foreign_keys AS fk
    INNER JOIN sys.foreign_key_columns AS fkc ON fk.object_id = fkc.constraint_object_id
    INNER JOIN sys.tables AS tp ON fkc.parent_object_id = tp.object_id
    INNER JOIN sys.columns AS cp ON fkc.parent_object_id = cp.object_id AND fkc.parent_column_id = cp.column_id
    INNER JOIN sys.tables AS tr ON fkc.referenced_object_id = tr.object_id
    INNER JOIN sys.columns AS cr ON fkc.referenced_object_id = cr.object_id AND fkc.referenced_column_id = cr.column_id
WHERE tp.name = '（資料表名稱）';
```
填入「（資料表名稱）」，可以找出所有參考此資料表的 Foreign Key 名稱、與每個 Foreign Key 的參考與被參考資訊。  
<br>

## 找出所有此資料表的 Foreign Key
```SQL
SELECT 
    fk.name AS 'Foreign Key 名稱',
    tp.name AS 'FK 參考 資料表',
    cp.name AS 'FK 參考 欄位',
    tr.name AS '被參考 資料表',
    cr.name AS '被參考 欄位'
FROM 
    sys.foreign_keys AS fk
    INNER JOIN sys.foreign_key_columns AS fkc ON fk.object_id = fkc.constraint_object_id
    INNER JOIN sys.tables AS tp ON fkc.parent_object_id = tp.object_id
    INNER JOIN sys.columns AS cp ON fkc.parent_object_id = cp.object_id AND fkc.parent_column_id = cp.column_id
    INNER JOIN sys.tables AS tr ON fkc.referenced_object_id = tr.object_id
    INNER JOIN sys.columns AS cr ON fkc.referenced_object_id = cr.object_id AND fkc.referenced_column_id = cr.column_id
WHERE 
    tp.name = '（資料表名稱）';
```
填入「（資料表名稱）」，可以找出所有此資料表的 Foreign Key 名稱、與每個 Foreign Key 的參考與被參考資訊。  
<br>

## 刪除 Foreign Key
```SQL
ALTER TABLE （資料表名稱）
DROP CONSTRAINT （FK 名稱）;
```
<br>

## 新增 Foreign Key
```SQL
ALTER TABLE （資料表）
ADD CONSTRAINT （FK 名稱） FOREIGN KEY (（此資料表的對應欄位名稱）)
REFERENCES （對方資料表） (（對方資料表的對應欄位名稱）);
```