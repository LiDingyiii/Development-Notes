#### 记录一次安卓开发

##### 环境搭建
    1. Android Studio(包括android SDK等组件的安装)
    2. Tauri v2-Beta
    3. Rust(Cargo)

##### 遇到的问题
######    1. Android实体机无法发送HTTP请求，虚拟设备没有问题
        
        需要在src-tauri\gen\android\app\src\main\AndroidManifest.xml的application标签中添加
        android:networkSecurityConfig="@xml/network_security_config"
        @xml/network_security_config位于
        src-tauri\gen\android\app\src\main\res\xml\network_security_config.xml
```XML 
    <?xml version="1.0" encoding="utf-8"?>
    <network-security-config>
        <base-config cleartextTrafficPermitted="true">
            <trust-anchors>
                <certificates src="system" />
            </trust-anchors>
        </base-config>
    </network-security-config>
```
######    2. APP签名过程
   
