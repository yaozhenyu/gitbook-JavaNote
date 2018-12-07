### 创建用户

```SQL
create user username with login password 'password';
```

### 创建数据库

```SQL
create database zhlc_bak;
```

### 授权

```
GRANT privilege [, ...] ON object [, ...] TO { PUBLIC | GROUP group | username }
```

eg:

```SQL
grant all on database database_name to user_name;
```

### 撤销授权



