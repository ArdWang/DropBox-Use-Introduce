# DropBox-Use-Introduce
This is DropBox Use Introduce

最近在使用DropBox做底层文件存储时使用的方法

### 注册

登入 https://www.dropbox.com/

然后绑定到自己的谷歌账号或者其它的账号都可以。

然后创建文件夹并放入文件



### 创建应用程序

https://www.dropbox.com/developers

点击 create app

选择自己的项目名称 以及权限如果不是使用到团队开发不需要使用团队的权限

注意以下两点：

**Generated access token**



**Access token expiration**

这个选择 No expiration 方便自己去测试 选择无限制的

### 官方文档

https://www.dropbox.com/developers/documentation/http/documentation#files-list_folder

获取文件夹中文件列表

```java
https://api.dropboxapi.com/2/files/list_folder
//post 请求

curl -X POST https://api.dropboxapi.com/2/files/list_folder \
    --header "Authorization: Bearer " \
    --header "Content-Type: application/json" \
    --data "{\"path\": \"/Homework/math\",\"recursive\": false,\"include_media_info\": false,\"include_deleted\": false,\"include_has_explicit_shared_members\": false,\"include_mounted_folders\": true,\"include_non_downloadable_files\": true}"
      
params:

{
    "path": "/Homework/math",
    "recursive": false,
    "include_media_info": false,
    "include_deleted": false,
    "include_has_explicit_shared_members": false,
    "include_mounted_folders": true,
    "include_non_downloadable_files": true
}

// 返回的数据
{
    "entries": [
        {
            ".tag": "file",
            "name": "bq1x.png",
            "path_lower": "/xxx/bq1x.png",
            "path_display": "/xxx/bq1x.png",
            "id": "id:bAq6xE76LawAAAAAAAAAGg",
            "client_modified": "2021-04-27T02:08:42Z",
            "server_modified": "2021-04-27T02:08:43Z",
            "rev": "015c0eabdd2f22900000002351f9b60",
            "size": 201717,
            "is_downloadable": true,
            "content_hash": "c2323d772917ec1cb549959cb388f5545927878f29f77e673e6dc20870f9816a"
        },
        {
            ".tag": "file",
            "name": "bq2x.png",
            "path_lower": "/xxx/bq2x.png",
            "path_display": "/xxx/bq2x.png",
            "id": "id:bAq6xE76LawAAAAAAAAAGw",
            "client_modified": "2021-04-27T03:10:57Z",
            "server_modified": "2021-04-27T03:10:57Z",
            "rev": "015c0eb9c6d898900000002351f9b60",
            "size": 71317,
            "is_downloadable": true,
            "content_hash": "a03175a956d6944d24ef9ca2e5b50db72ee53aa0194f89e091cbe5d30cd743a7"
        }
    ],
    "cursor": "AAFtnY1bSAOuiv2C9mVwxF3jLIf9aNkShoV7Sorf0IFDBBT4NtHE3GbO2QXqYNYT88eH9infgNOAFE1kOHd77xuVgXuades8xSL63bxVJQ39rdtYvqgtE7juEqvileRERWGIwIDByOBkplj4cjYTzircrkQT2JrC28ctQJfuD6urPTfolzL7psT6AhApH0qnQcb5FJKgwEKp2MKalmZCEJUl",
    "has_more": false
}

```



要注意的问题：

下载文件的时候需要传入 

Header中 Dropbox-API-Arg {"path":"tt/xx.txt"} 记得 把path这个数据转为json的数据 不然请求的时候老是报错

