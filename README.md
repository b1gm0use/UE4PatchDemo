# UE4PatchDemo

## 项目说明

本项目是一个 UE4 热更包构建的示例工程，使用的原始资源和代码均来自于 UE 官方。在 4.27.2 Launcher 版本下测试通过。

测试构建可以使用两种方法，一是 Project Launcher 方法，操作起来稍微有些繁琐，但是不需要使用命令行；二是 RunUAT 方法，操作简单，但是需要一定的命令行构建知识。

## 使用 Project Launcher 进行构建

### 构建基础包

1. 首先将此版本库更新到 [Make base package](https://github.com/b1gm0use/UE4PatchDemo/commit/e3aba2d44d83d3188f1213360d1f14177828f5fe) (SHA1: e3aba2d44d83d3188f1213360d1f14177828f5fe) 这次提交，可以使用如下命令：
   ```bat
   git reset --hard e3aba2d44d83d3188f1213360d1f14177828f5fe
   ```
2. 将 `Profiles/BASEPACKAGE_73D789484848EFF90B71ED8D289FCF8A.ulp2` 文件复制到 `引擎根目录\Programs\UnrealFrontend\Profiles\` 下
3. 使用 Unreal Editor 打开工程
4. 打开 Project Launcher
5. 在下方的 Custom Launch Profile 里会有一个 `BasePackage` 的项目，编辑此项目的 Project 地址为项目的 UProject 文件位置
6. 返回到 Project Launcher 首页，启动 `BasePackage`
7. 结束后完成基础包构建
8. 启动 `Saved\StagedBuilds\WindowsNoEditor\UE4PatchDemo` 下的可执行文件，可以正常运行游戏。



### 构建第一个热更包

1. 将此版本库更新到 [Make Patch1](https://github.com/b1gm0use/UE4PatchDemo/commit/457520e020bdbf9a6b1c62311d60c10c5cb6fa29) (SHA1: 457520e020bdbf9a6b1c62311d60c10c5cb6fa29) 这次提交，可以在 cmd 使用如下命令：
   ```bat
   git reset --hard 457520e020bdbf9a6b1c62311d60c10c5cb6fa29
   ```
2. 将 `Profiles/PATCH1_A48951124CA0CC11A7FC5FB5C1C8F932.ulp2` 文件复制到 `引擎根目录\Programs\UnrealFrontend\Profiles\` 下
3. 仿照基础包中的操作，启动 `Patch1`
4. 结束后完成第一个热更包的构建
5. 启动 `Saved\StagedBuilds\WindowsNoEditor\UE4PatchDemo` 下的可执行文件，可以看到在玩家左侧的场景中出现了一个新的几何体。

### 构建第二个热更包

1. 将此版本库更新到 [Make Patch2](https://github.com/b1gm0use/UE4PatchDemo/commit/dbd8847483ad98675b2c677176bbc6efdd00618a) (SHA1: dbd8847483ad98675b2c677176bbc6efdd00618a) 这次提交，可以在 cmd 使用如下命令：
    ```bat
        git reset --hard dbd8847483ad98675b2c677176bbc6efdd00618a
    ```
2. 将 `Profiles/PATCH2_18A06C44452033C008EC6A9DE778F71E.ulp2` 文件复制到 `引擎根目录\Programs\UnrealFrontend\Profiles\` 下
3. 仿照基础包中的操作，启动 `Patch2`
4. 结束后完成第二个热更包的构建
5. 启动 `Saved\StagedBuilds\WindowsNoEditor\UE4PatchDemo` 下的可执行文件，可以看到在玩家左侧的地面上出现了一个爆炸特效，大概持续3秒左右。


## 使用 RunUAT 进行构建

### 构建基础包

1. 首先将此版本库更新到 [Make base package](https://github.com/b1gm0use/UE4PatchDemo/commit/e3aba2d44d83d3188f1213360d1f14177828f5fe) (SHA1: e3aba2d44d83d3188f1213360d1f14177828f5fe) 这次提交，可以使用如下命令：
   ```bat
   git reset --hard e3aba2d44d83d3188f1213360d1f14177828f5fe
   ```
2. 在 cmd 下运行如下命令（注意替换相关的地址参数）：

   ```bat
   "C:\Epic Games\UE_4.27\Engine\Build\BatchFiles\RunUAT.bat" -ScriptsForProject=D:/UE4PatchDemo/UE4PatchDemo.uproject BuildCookRun -project=D:/UE4PatchDemo/UE4PatchDemo.uproject -noP4 -clientconfig=Development -serverconfig=Development -nocompile -nocompileeditor -installed -ue4exe="C:\Epic Games\UE_4.27\Engine\Binaries\Win64\UE4Editor-Cmd.exe" -utf8output -platform=Win64 -targetplatform=Win64 -build -cook -map= -unversionedcookedcontent -pak -createreleaseversion=1.0 -manifests -SkipCookingEditorContent -compressed -stage -package
   ```

3. 结束后完成基础包构建
4. 启动 `Saved\StagedBuilds\WindowsNoEditor\UE4PatchDemo` 下的可执行文件，可以正常运行游戏。


### 构建第一个热更包

1. 将此版本库更新到 [Make Patch1](https://github.com/b1gm0use/UE4PatchDemo/commit/457520e020bdbf9a6b1c62311d60c10c5cb6fa29) (SHA1: 457520e020bdbf9a6b1c62311d60c10c5cb6fa29) 这次提交，也可以使用如下命令：
   ```bat
   git reset --hard 457520e020bdbf9a6b1c62311d60c10c5cb6fa29
   ```

2. 在 cmd 下运行如下命令（注意替换相关的地址参数）：

   ```bat
    "C:\Epic Games\UE_4.27\Engine\Build\BatchFiles\RunUAT.bat" -ScriptsForProject=D:/UE4PatchDemo/UE4PatchDemo.uproject BuildCookRun -project=D:/UE4PatchDemo/UE4PatchDemo.uproject -noP4 -clientconfig=Development -serverconfig=Development -nocompile -nocompileeditor -installed -ue4exe="C:\Epic Games\UE_4.27\Engine\Binaries\Win64\UE4Editor-Cmd.exe" -utf8output -platform=Win64 -targetplatform=Win64 -build -cook -map= -unversionedcookedcontent -pak -createreleaseversion=1.1 -generatepatch -basedonreleaseversion=1.0 -stagebasereleasepaks -addpatchlevel -manifests -SkipCookingEditorContent -compressed -stage -package
   ```

3. 结束后完成第一个热更包的构建
4. 启动 `Saved\StagedBuilds\WindowsNoEditor\UE4PatchDemo` 下的可执行文件，可以看到在玩家左侧的场景中出现了一个新的几何体。

### 构建第二个热更包

1. 将此版本库更新到 [Make Patch2](https://github.com/b1gm0use/UE4PatchDemo/commit/dbd8847483ad98675b2c677176bbc6efdd00618a) (SHA1: dbd8847483ad98675b2c677176bbc6efdd00618a) 这次提交，也可以使用如下命令：
   ```bat
   git reset --hard dbd8847483ad98675b2c677176bbc6efdd00618a
   ```
2. 在 cmd 下运行如下命令（注意替换相关的地址参数）：

   ```bat
    "C:\Epic Games\UE_4.27\Engine\Build\BatchFiles\RunUAT.bat" -ScriptsForProject=D:/UE4PatchDemo/UE4PatchDemo.uproject BuildCookRun -project=D:/UE4PatchDemo/UE4PatchDemo.uproject -noP4 -clientconfig=Development -serverconfig=Development -nocompile -nocompileeditor -installed -ue4exe="C:\Epic Games\UE_4.27\Engine\Binaries\Win64\UE4Editor-Cmd.exe" -utf8output -platform=Win64 -targetplatform=Win64 -build -cook -map= -unversionedcookedcontent -pak -createreleaseversion=1.2 -generatepatch -basedonreleaseversion=1.0 -stagebasereleasepaks -addpatchlevel -manifests -SkipCookingEditorContent -compressed -stage -package
   ```

3. 结束后完成第二个热更包的构建
4. 启动 `Saved\StagedBuilds\WindowsNoEditor\UE4PatchDemo` 下的可执行文件，可以看到在玩家左侧的地面上出现了一个爆炸特效，大概持续3秒左右。
