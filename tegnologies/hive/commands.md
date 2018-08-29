# Hive. Comandos

En este archivo se veran algunos comandos basicos de Hive, como se puede ver son todos muy parecidos a SQL:

* **Comandos DDL**: Nos permiten definir y borrar objetos.

    - Create/Drop/Truncate TABLE
    - Create/Drop/Alter/Use DATABASE
    - Alter Table/Patition/Column
    - Create/Drop/Alter View
    - Create/Drop/Alter Index
    - Create/Drop Macro

* **Comandos DML**: De manipulacion de datos.
    
    - LOAD
    - INSERT
    - UPDATE
    - DELETE
    - MERGE

* **Comandos Select** -> Estos comandos son muy parecidos a SQL y sirven para hacer consultas contra la base de datos.

    ```
    SELECT [ALL | DISTINCT] select_expr, select_expr...
    FROM table_ref
    [WHERE where_condition]
    [GROUP BY col_list]
    [HAVING having_condition]
    [CLUSTER BY col_list ...]
    [LIMIT number]
    ;
    ```

* **Otras utilidades** ->

    - Mathematical Functions
    - Collection Functions
    - Type Converion Functions
    - Date Functions
    - Conditional Functions
    - String Functions
    - Misc Functions
