# 利用python加walle
# 一键完成Release Apk的打包、签名、加固、打渠道包全流程

> MakeChannelByWalle360



## 说明

### 前置条件

App的签名信息需要在build.gradle的buildTypes中配置好，否则打出来的渠道包是未签名的。



### 配置项，不可遗漏任何一条

> build.gradle需要增加：

apply plugin: 'com.gongva.plugin'


> build.gradle需要增加基础工具配置：

channel {

    path360 "本地电脑的360加固的“jiagu”目录全路径，目录层级使用双斜杠“\\”分隔，如：F:\\Develop\\360jiagubao_windows_64\\jiagu"

    sdkBuildToolPath "本地电脑的Android build-tools指定版本目录的全路径，如：F:\\Develop\\sdk\\build-tools\\28.0.3"

    appName "需要打包的Module名字，如：app"

}


> 在walle根目录下放入签名文件

拷贝文件，如:keystore.jks


> 在walle下changeParam配置360登录账号与签名文件的密码配置

name360 = "360登录的账号，如：xx@xx.com"

password360 = "360登录的密码"


keystoreName = "签名文件名称，如:keystore.jks"

keyAlias = "根据自身签名填写"

keystorePassword = "根据自身签名填写"

keyPassword = "根据自身签名填写"


> 在walle下channel文件填写需要写入的渠道清单，一行表示一个渠道

如：

360

yingyongbao

huawei

xiaomi


> 最后执行AS右侧Gradle中，gongva分组下的makeChannel

过程大致需要几分钟，渠道apk输出目录在walle/channel目录下