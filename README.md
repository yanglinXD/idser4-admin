# Idser4

## 数据库迁移

在根目录下`build`文件夹中有迁移数据库的`powershell`脚本，按下方顺序执行迁移：

- add migration

```sh
.\add-migrations.ps1 -migration DbInit -migrationProviderName PostgreSQL
```

- update database

```sh
.\update-database.ps1 -migrationProviderName PostgreSQL
```
