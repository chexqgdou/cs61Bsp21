一、 github仓库的配置
1. 在本地新建一个文件夹，比如我的：D:\cs61Bsp21；

Bash
Administrator@WIN-20250328BND MINGW64 ~
$ cd d:

Administrator@WIN-20250328BND MINGW64 /d
$ cd cs61bsp21

Administrator@WIN-20250328BND MINGW64 /d/cs61bsp21 (master)
$


2. 我用的自带的git bash，进入第一步的文件夹，
输入：git init
是初始化文件夹代表被git控制的意思；

3.接着输入git remote add skeleton https://github.com/Berkeley-CS61B/skeleton-sp21，这个是ucb的仓库，我们现在做的是连接这个远程仓库，后面将我们要的框架代码拉到本地；

4. 然后输入git pull skeleton master将框架代码拉到你的文件夹中；

这是你会看到本地目录已经拉取了文件，但是libary-sp21目录下是空的。

原因：因为 library-sp21 目录在仓库中是作为 Git 子模块（submodule） 存在的，而普通的 git clone 或 git remote add + pull 操作不会自动下载子模块的内容。

原因说明：Git 子模块允许一个 Git 仓库作为另一个 Git 仓库的子目录存在，同时保持各自的版本控制。在 skeleton-sp21 仓库中，library-sp21 是一个子模块，它指向另一个独立的仓库（https://github.com/Berkeley-CS61B/library-sp21）。因此，当你克隆主仓库或拉取代码时，只会下载子模块的引用信息（如指向的仓库地址和 commit ID），而不会自动下载子模块的实际内容，导致目录为空。

解决方法：
要获取 library-sp21 的内容，需要手动初始化并更新子模块，执行以下命令：

1.进入你的本地仓库目录（D:\CS61Bsp21）：
cd D:\CS61Bsp21

2.初始化子模块（仅首次需要）：
bash
git submodule init
3.更新子模块内容（拉取实际代码）：
bash
git submodule update
执行后，library-sp21 目录就会被填充实际内容。
补充说明：
如果后续主仓库更新了子模块的引用（如指向新的 commit），你需要再次执行 git submodule update 来同步最新的子模块内容。
