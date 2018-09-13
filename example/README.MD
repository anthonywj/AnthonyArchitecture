##使用CC组件如何单独编译
```groovy
//默认的作为application运行时Manifest文件路径
            def debugManifest = 'src/main/debug/AndroidManifest.xml'
            if (runAsApp && project.file(debugManifest).exists()) {
                manifest.srcFile debugManifest
            } else {
                manifest.srcFile 'src/main/AndroidManifest.xml'
                //集成开发模式下自动排除debug文件夹中的所有Java文件
                // 可以将debug代码放在这个包内，例如：Application子类
                java {
                    exclude 'debug/**'
                }
            }
            // 注：2018-03-12推荐：将组件单独以app运行时的测试代码及资源放到src/main/debug/目录下
            if (runAsApp) {
                //debug模式下，如果存在src/main/debug/assets，则自动将其添加到assets源码目录
                if (project.file('src/main/debug/assets').exists()) {
                    assets.srcDirs = ['src/main/assets', 'src/main/debug/assets']
                }
                //debug模式下，如果存在src/main/debug/java，则自动将其添加到java源码目录
                if (project.file('src/main/debug/java').exists()) {
                    java.srcDirs = ['src/main/java', 'src/main/debug/java']
                }
                //debug模式下，如果存在src/main/debug/res，则自动将其添加到资源目录
                if (project.file('src/main/debug/res').exists()) {
                    res.srcDirs = ['src/main/res', 'src/main/debug/res']
                }
            }
```            
            
根据CC-Setting这段代码，在src/main/目录下新建debug目录，
单独运行时：
	1.使用debug目录下的AndroidManifest.xml;
	2.debug目录下的java,assets,res添加到常规目录下

## 资源冲突解决
```
resourcePrefix "example_"
```
 
 之后需要手动吧颜色资源，String资源，图片，xml等加上example_前缀
 
 
 ##Markdown 新手指南
 ![]https://www.jianshu.com/p/q81RER