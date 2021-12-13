基于密码模式+Spring Security OAuth2+JWT的最简授权服务器
======

# 操作方式

### 1. 启动jwt-authserver，端口8080

### 2. 启动jwt-resourceserver，端口8081

### 3. 获取JWT令牌

curl -X POST --user hugeSpa:112233 http://localhost:8080/oauth/token -H "accept: application/json" -H "content-type: application/x-www-formurlencoded" -d "grant_type=password&username=dx&password=ddd&scope=read_userinfo"

响应案例：

```json
{
  "access_token": "geyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2Mzk0MjY3NTcsInVzZXJfbmFtZSI6ImR4IiwiYXV0aG9yaXRpZXMiOlsiUk9MRV9VU0VSIl0sImp0aSI6ImJjZTZmNGExLTNlNGQtNDc4Mi05NDgwLWViYmEzZGQ5NzA3YSIsImNsaWVudF9pZCI6Imh1Z2VTcGEiLCJzY29wZSI6WyJyZWFkX3VzZXJpbmZvIl19.lW_11CPIDeu4Yjc6LS4EFYZaibtKBi0hqFg2kJTuYo",
  "token_type": "bearer",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX25hbWUiOiJkeCIsInNjb3BlIjpbInJlYWRfdXNlcmluZm8iXSwiYXRpIjoiYmNlNmY0YTEtM2U0ZC00NzgyLTk0ODAtZWJiYTNkZDk3MDdhIiwiZXhwIjoxNjQxOTc1NTU3LCJhdXRob3JpdGllcyI6WyJST0xFX1VTRVIiXSwianRpIjoiYjU2ZTQwYjYtNmQxMi00YmUzLTk5NDgtODY3NmY1NDg4NWU3IiwiY2xpZW50X2lkIjoiaHVnZVNwYSJ9.h4mGIy0tracVXRZ6vFsC2QQ7ZtVKqey7FxJOKmrp-1Q",
  "expires_in": 43199,
  "scope": "read_userinfo",
  "jti": "bce6f4a1-3e4d-4782-9480-ebba3dd9707a"
}
```

### 4. 调用API

curl -X GET http://localhost:8081/api/userinfo -H "authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2Mzk0MjY3NTcsInVzZXJfbmFtZSI6ImR4IiwiYXV0aG9yaXRpZXMiOlsiUk9MRV9VU0VSIl0sImp0aSI6ImJjZTZmNGExLTNlNGQtNDc4Mi05NDgwLWViYmEzZGQ5NzA3YSIsImNsaWVudF9pZCI6Imh1Z2VTcGEiLCJzY29wZSI6WyJyZWFkX3VzZXJpbmZvIl19.lW_11CPIDeu4Yjc6LS4EFYZaibtKBi0hqFg2kJTuYog"

案例响应：

```json
{
  "name": "dx",
  "email": "dx@yzw.com"
}
```