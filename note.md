## 记录修改点

暂时不支持 MP4 

### 修改 getBaseUrl 用于支持视频地址的多级目录
```js
getBaseUrl(file) {
// 用于支持多级的目录
const sourceURL = this.options.sourceURL;
const isAbsolute = file.indexOf("//") > -1;
if (!isAbsolute) {
    const isAbsoultStart = file.indexOf("/") == 0;
    if (isAbsoultStart) {
    //sourceURL.replace(/^https?://[^/]*/,'$1')
    return sourceURL.match(/^https?:\/\/[^\/]*/g)[0];
    } else {
    const lastSlash = sourceURL.lastIndexOf("/");
    return sourceURL.substr(0, lastSlash + 1);
    }
}
return "";
}
```

### 在本地运行使用ngxin运行项目，配置 nginx.conf
<!-- 添加server -->
```sh
server {
    listen       9000;
    location / {
        root   D:/1wxx/workspace/h265player-test;
        index  index.html index.htm;
        autoindex on;
    }
}
```