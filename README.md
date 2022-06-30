
# SageTools

#### 介绍

SageTools 一个简单的常用工具类和拓展方法包


#### 安装教程


#### 使用说明

##### 结合CI/CD自动化发布
为了使发布更加方便，我编写了`SageTools.Console`项目用于快速发布，其原理很简单，仅仅是改变了`xml`文件的内容.
```
dotnet publish SageTools.Console/SageTools.Console.csproj -o pack -c Release
dotnet pack/SageTools.Console.dll -source="../SageTools/SageTools.csproj" -version="${CI_COMMIT_REF_NAME}"
dotnet build SageTools/SageTools.csproj -c Release
dotnet pack SageTools/SageTools.csproj -o pack -c Release
dotnet nuget push pack/SageTools.${CI_COMMIT_REF_NAME}.nupkg -s https://api.nuget.org/v3/index.json -k Your ApiKey
```
其中`${CI_COMMIT_REF_NAME}`为本次发布版本号，可以根据你使用的环境自行更改；`Your ApiKey`为你的Nuget ApiKey

我通过给分支打标签触发构建行为，标签名为版本，比如新建标签`1.0.1`，此时对应的命令应该为：
```
dotnet publish SageTools.Console/SageTools.Console.csproj -o pack -c Release
dotnet pack/SageTools.Console.dll -source="../SageTools/SageTools.csproj" -version="1.0.1"
dotnet build SageTools/SageTools.csproj -c Release
dotnet pack SageTools/SageTools.csproj -o pack -c Release
dotnet nuget push pack/SageTools.1.0.1.nupkg -s https://api.nuget.org/v3/index.json -k Your ApiKey
```

#### 参与贡献


#### 计划中的功能



#### 详细功能


