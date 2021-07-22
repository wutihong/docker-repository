# osslsigncode-java
使用开源的[osslsigncode](https://github.com/mtrojnar/osslsigncode/releases/tag/2.1),整合jdk8，形成Dockerfile文件，供项目进行文件签名部署。

> 快速使用

```shell
docker run -n name wutihong/osslsigncode-jdk8:latest
```

* 由于jdk文件超过100M，不允许上传，请自行选择对应的jdk版本进行替换，修改Dockerfile中关于jdk相关配置即可
