# 黑苹果EFI配置

GA-B150M-D3H GTX 10X0 macOS High Sierra
日常使用正常，显卡，声卡，网卡都正常工作。

## 兼容硬件

### 主板 
	GA-B150M-D3H
### CPU 
	Intel  6代 Skylake 平台 （i3 6100，i5 6500，i7 6700  ）
### 显卡  
	GTX 10X0系列 （1050 1060 1070 1080 ）
	
## OSX版本
	macOS High Sierra
	由于Nvdia在10.13之后停止了显卡驱动的提供，
	因此最高使用10.13.6 (17G66)
	
	
## 显卡的安装（17G66）
### 下载安装包 
官方驱动不支持17G66版本，下载官方的 [最后的版本]
	(https://images.nvidia.com/mac/pkg/387/WebDriver-387.10.10.10.40.133.pkg), 修改包中的Distribution文件。

### 修改安装包
WebDriver-17G66中放了修改后的版本，可以直接修改，跳过这段。
	 function InstallationCheck() 
       {            
            if (!validateSoftware()) return false; #删除这一行
            return true;
       }
       
       function validateSoftware()
        {
            var supportedOSVer = "10.13.6";
            var supportedOSBuildVer = "17G66"; #修改为17G66
            var targetBuild = system.version.ProductBuildVersion; 
            var result = compareBuildVersions(targetBuild, supportedOSBuildVer);
### 安装后修改TEXT文件
找到/Library/Extensions/NVDAStartupWeb.kext ，将文件拷贝到桌面， 右键显示包内容，打开文件夹Contents, 修改Info.plist文件。
	
	将节点NVDARequiredOS的值修改成17G66
修改后覆盖回去，使用kext_utility修复权限。