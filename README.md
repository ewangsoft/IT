这里是我使用OpenWrt的记录。
1、将OpenWrt源和相关packages下载到本地：
    1）git clone https://github.com/openwrt/openwrt.git  //将OpenWrt源下载到当前openwrt目录，并自动创建和切换到本地分支master
    2）cd openwrt
    3）./scripts/feeds update -a & ./scripts/feeds install -a  //将附带packages源下载到本地
2、查看当前本地分支：git branch；查看当前远程分支：git branch -r ；一次查看所有分支：git branch -a
3、创建远程分支 origin/openwrt-19.07的本地分支1907：git branch 1907  origin/openwrt-19.07
4、当从本地master分支切换到1907分支时，如果修改了本地master分支，需要先使用git stash save贮藏下变动（官方文档推荐用push：https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E8%B4%AE%E8%97%8F%E4%B8%8E%E6%B8%85%E7%90%86 ，但我在git=2.7.4版本下没找到push参数）
5、切换到当前稳定版分支：git checkout 1907
6、更新稳定分支1907的packages：./scripts/feeds update -a & ./scripts/feeds install -a 
7、修改./scripts下的download.pl,添加相关镜像源，可参考这里：https://github.com/coolsnowwolf/lede/commit/e5f08410e0b27af9a8a3655161083a5a525ff903
8、在master和1907分支下执行make menuconfig来选择自己需要的软件包后就可以编译定制固件了。
