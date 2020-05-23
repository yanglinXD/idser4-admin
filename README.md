# idser4-admin

## 安装客户端依赖包

```sh
cd src/Skoruba.IdentityServer4.Admin
yarn

cd src/Skoruba.IdentityServer4.STS.Identity
yarn
```

## 数据库迁移

### 修改数据库连接配置

> 修改下方项目下的`appsettings.json`文件

- Skoruba.IdentityServer4.Admin
- Skoruba.IdentityServer4.Admin.Api
- Skoruba.IdentityServer4.STS.Identity

```
"ConnectionStrings": {
  // db connection string
}
```

### 修改数据库类型

```
"DatabaseProviderConfiguration": {
  "ProviderType": "PostgreSQL"
}
```

### 执行迁移脚本

> 在根目录下`build`文件夹中有迁移数据库的`powershell`脚本，按下方顺序执行迁移：

- add migration

```sh
.\add-migrations.ps1 -migration DbInit -migrationProviderName PostgreSQL
```

- update database

```sh
.\update-database.ps1 -migrationProviderName PostgreSQL
```

## 项目结构

- 界面与 API
  - Skoruba.IdentityServer4.Admin -- 管理员界面
  - Skoruba.IdentityServer4.Admin.Api -- API 与 Swagger
  - Skoruba.IdentityServer4.STS.IdentityServer4 -- 身份认证与个人用户界面
- 业务逻辑层
  - Skoruba.IdentityServer4.Admin.BusinessLogic -- 包含公共的服务、事件、模型映射器、Dto
  - Skoruba.IdentityServer4.Admin.BusinessLogic.Identity -- 包含服务、事件、模型映射器、Dto
  - Skoruba.IdentityServer4.Admin.BusinessLogic.Shared -- 共享的 Dto 与异常类
- 数据访问层
  - Skoruba.IdentityServer4.Admin.EntityFramework -- EF Core 数据访问层
  - Skoruba.IdentityServer4.Admin.EntityFramework.Identity -- 仓储层
  - Skoruba.IdentityServer4.Admin.EntityFramework.Extensions -- 数据访问层的相关扩展
  - Skoruba.IdentityServer4.Admin.EntityFramework.Shared -- 数据库上下文、Identity 实体与日志记录
- EF Core 迁移层
  - Skoruba.IdentityServer4.Admin.EntityFramework.SqlServer
  - Skoruba.IdentityServer4.Admin.EntityFramework.MySql
  - Skoruba.IdentityServer4.Admin.EntityFramework.PostgreSQL
- 单元测试
  - Skoruba.IdentityServer4.Admin.IntegrationTests -- 管理界面的集成测试
  - Skoruba.IdentityServer4.Admin.Api.IntegrationTests -- API 的集成测试
  - Skoruba.IdentityServer4.Admin.UnitTests -- 管理界面的单元测试
  - Skoruba.IdentityServer4.STS.IntegrationTests -- 身份认证的集成测试

## 其他

[查看更多](./Skoruba.IdentityServer4.Admin.md)
