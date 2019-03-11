# [mysql] 컬럼 있는지 체크

1. show columns

   ```sql
   SHOW COLUMNS FROM `user` LIKE 'user_id';
   ```

1. Information_schema.columns

   ```sql
   SELECT 1
   FROM Information_schema.columns
   WHERE table_schema = 'DB'
     AND table_name = '테이블명'
     AND column_name = '컬럼명'
   ```
