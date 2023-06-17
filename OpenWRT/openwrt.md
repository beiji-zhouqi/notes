# OpenWRT

### 编译
1. 准备系统空间足够大
    
    (可选）增加一个非Root但有sudo权限的账户，例如：openwrt

    $adduser openwrt

    $usermod -a -G sudo openwrt

    $su openwrt

2. 安装编译必需的依赖 注意：必备依赖libssl-dev版本冲突

    $sudo apt update

    $sudo apt upgrade

    $sudo apt install build-essential clang flex g++ gawk gcc-multilib gettext git 
libncurses5-dev python3-distutils rsync unzip zlib1g-dev file wget

3. 拉取OpenWrt项目源码

    $cd ~

    $git clone -b openwrt-22.03 https://github.com/openwrt/openwrt.git

4. 编译前准备

    $./scripts/feeds update -a

    $./scripts/feeds install -a    //出现警告多执行几次

    $make menuconfig    //定制自己的版本

5. 开始编译

    注意：网络不好可以预先运行 make download
    
    $make -j4 V=s

6. 再次编译的准备
    
    $make clean       //仅清理bin目录
    
    $make dirclean    //清理除了.config、dl文件夹和feeds以外所有编译文件
    
    $make distclean   //完全清理干净，一键回到刚git clone下来的时候
    
    $make defconfig   //对配置文件.config进行了调整，则需要执行该命令来调整配置文件