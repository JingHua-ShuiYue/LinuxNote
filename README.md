# LinuxNote
#### Linux的目录结构:

1. Linux只有一个根目录。

2. 层级式的目录结构:

   - **bin ->usr/bin:**系统的可执行文件，可以在任何目录下执行

   - **usr/local/bin:**用户自已的可执行文件，可以在任何目录下执行

   - **etc:**存放配置文件。配置环境变量(/etc/profile)。

   - **home:**每一个用户的根目录，用来保存用户私人的数据，默认情况下，目录名和自己的用户名相同。

   - **opt:**存档额外安装的软件，相当于windows系统的中Program files目录。

     更多：[Linux根目录下文件的作用](.\超链接文件\Linux下各目录的作用.html)

     注：找链接按住ctrl点击打开

#### Linux的远程操作:

1. Xshell: Linux 的终端模拟软件。

   - 安装并破解:解压、破解(运行两个.bat文件)、启动(Xshell)

   - 连接远程Linux系统:创建会话:

   - 查看Linux系统的ip地址: ifconfig
2. xftp:文件传输软件。

   - 安装并破解:解压、破解(运行两个.bat文件)、启动(Xftp)
   - 连接远程Linux系统:创建会话:
   - 查看Linux系统的ip地址: ifconfig

#### vi和vim:

- 是Linux中的文本编辑器，用来在Linux中查看或者编辑文本文件，就好像windows中的记事本一样。

- vim是vi的增强版本，vi 的绝大多数用法在vim都适用。

  ```
  mkdir 文件夹名字  ----  创建新目录
  ls  ----  展示当前文件夹中的文件
  cd 文件  ----  跳转到该文件夹下
  vim/vi 文件.类型  ----  用vim/vi文本编辑器打开该文件，如果文件不存在则创建该文件
  ```

- vi和vim的使用:

  - 一般模式:

    用vi或者vim命令打开文件(vim test.txt),  进入了一般模式,，可以查看文件的内容，并且可以通过上下左右键移动光标，查看文件某一部分;但是不能编辑文件内容。

  - 编辑模式:

    在一般模式下，按i键或者a键，进入编辑模式;可以编辑文件内容;但是不能保存编辑的内容;
    按Esc键，可以回到一般模式。

  - 命令模式:

    命令模式:在一般模式下，按shift + :    进入命令模式

    - q!   ----   不保存强制退出
    - wq   ----   保存并退出编辑器
    - q  -----      只是退出编辑器

- vi和vim编辑器的快捷键:

  - 复制当前行:

    在一般模式下，按yy，把光标所在行复制到剪切板按p，把剪切板中的内容粘贴到光标所在的下一行。

  - 复制当前行往下5行:

    在一般模式下，按5yy，把光标所在行往下5行复制到剪切板按p，把剪切板中的内容粘贴到光标所在的下一行。

  - 在文本文件中查找关键字:

    在命令行模式下，输入/关键字，回车按n表示光标查找下一个关键字

  - 删除光标所在的当前行:

    在一般模式下，按dd，删除光标所在的当前行

  - 删除光标所在的行往下5行:

    在一般模式下，按5dd

  - 撤销上一个动作

    一般模式下按 u

  - 命令行模式下，设置文件的行号，取消文件的行号.

    命令行下set nu和set nonu

- 输出重定向

  - \>    -----  会覆盖文件原内容
  - \>>  -----  文件末尾追加 不会覆盖文件

- 代码着色

  - 显示颜色：“：syntax  on”
  - 关闭显示颜色：“：syntax off”


#### Linux中的用户管理

1. 任何使用Linux的系统资源的用户，必须使用一个合法的账号和密码，账号和密码一般都是向系统管理员申请。root是Linux系统安装时默认创建的系统管理员账号，由root创建普通账号。

2. 添加用户: useradd  [选项]  用户名

   ```
   useradd lisi //创建一个用户lisi
   ```

   - 在/home目录下创建用的根目录，目录名称默认跟用户名相同

   - 在Linux中任何一个用户都至少属于一个组，新建用户时如果不指定组，则会新建一个组，组名跟用户名相同，并且把该用户添加到该组中。

     ```
     useradd -d /home/ww wangwu 	------------- 创建用户的同时，指定用户的根目录 
     ```

3. 给用户设置密码:passwd  用户名

   ```
   passwd  lisi       密码要满足一定的复杂度
   ```

4. 删除用户: userdel  用户名

   ```
   userdel  lisi
   userdel  -r  lisi   ------------- 删除用户的同时级联删除它的主目录
   ```

5. 查看用户信息: id  用户名

6. 显示当前登陆的用户名：whoami

   - 一般用于shell脚本，用于获取当前操作的用户名方便记录日志。

7. 操作服务器的主机名（读取）：hostname

   ```
   语法1：hostname
   含义：输出完整的主机名id  zhangsan
   语法2：hostname -f
   含义：表示输出当前主机名中的FQDN（全限定域名），看作是域名就可以了。
   ```

8. 切换用户: su  用户名

   ```
   su  zhangsan
   ```

   -  从权限高的用户切换权限低的用户，不需要密码验证;

   -  从权限低的用户切换到权限高的用户，必须密码验证。

#### Linux中组的管理

- Linux中的组相当于角色的概念，可以对有共性的用户进行统一管理;
- 每一个用户至少属于一个组，不能独立于组存在，也可以属于多个组;
- 新建用户时如果不指定组，则会新建一个组，组名跟用户名相同，并且把该用户添加到该组中。

---

1. 添加组: groupadd  组名

   ```
   groupadd  dev
   ```

2. 删除组: groupdel  组名

   ```
   groupdel  dev
   ```

3. 把用户添加到组中: gpasswd  -a  用户名  组名

   ```
   gpasswd  -a  zhangsan  dev
   ```

4. 把用户从组中移除: gpasswd  -d  用户名  组名

   ```
   gpasswd  -d  zhangsan  dev
   ```

5. 添加用户时，指定所属的组(主组): useradd  -g  组名  用户名

   ```
   useradd  -g  dev  lisi
   ```

#### Linux中的系统操作命令:

1. 关机:

   - shutdown  now ---- 立即关机
   - shutdown  -h  XXX ---- 定时关机
   - shutdown  -r  now ---- 立即重启
   - init 0  ----  关机
   - poweroff   ----  关机  
   - halt  -p  ----  关闭内存

2. 重启：reboot ---- 立即重启

3. 同步数据库：sync

4. 查看服务器的进程占的资源：top指令

   语法：#top   （动态显示）    //退出显示：按q键或者ctrl+c

   ```
   us 用户空间占用CPU百分比
   sy 内核空间占用CPU百分比
   ni 用户进程空间内改变过优先级的进程占用CPU百分比
   id 空闲CPU百分比
   wa 等待输入输出的CPU时间百分比
   hi 硬件中断
   si 软件中断 
   st: 实时
   
   PID：进程id
   USER：该进程对应的用户
   PR：进程的优先级。优先级越大，越优先执行。
   VIRT：虚拟内存。（chrome进程，想运行这个浏览器，要打开这个进程，需要申请内存，先申请500MB。实际使用320MB，那么虚拟内存就是500MB）
   RES：常驻内存（申请了500MB，实际使用320MB，那么常驻内存就是320MB）
   SHR: 共享内存（抽象。申请了500MB，但实际使用了320MB，但是如果其中包含了对其他进程的调用开销，则需要扣除） 
   计算一个进程实际使用的内存=常驻内存-共享内存
   S:表示进程的状态（sleeping）
   R：表示运行（running）
   %cpu：表示CPU的占用百分比
   %MEM：表示内存的占用百分比
   TIME+：执行的时间
   COMMAND：进程的名称或者路径
   
   在运行top的时候，可以按下方便的快捷键
   M：表示将结果按照内存（MEM）从高到低进行降序排列
   P：表示将结果按照CPU使用率从高到低进行降序排列
   1：当服务器拥有多个CPU的时候可以使用“1”快捷键来切换是否展示各个CPU的详细信息。
   ```

5. 查看目录的真实大小：du -sh

   - 语法：#du –sh 目录路径

     选项含义：

     - -s：只显示汇总的大小
     - -h: 表示以较高可读性的形式显示

6. 查看磁盘的空间：df指令

   语法：#df  –h   -h表示以可读性较高的形式展示大小

7. 查看内存使用情况: free -m

   语法：#free –m     //-m以兆为单位查看

8. 统计文件内容信息（包括：行数、单词数、字节数）：wc

   语法：#wc –lwc 需要统计的文件路径

   - -l：表示lines  适用

   - -w：表示words  主要是对英文适用

   - -c:表示bytes

#### Linux中的帮助命令

1. 用来查看Linux系统手册上的帮助信息: man  命令
   man  ls
   分屏显示、按回车翻一行、按空格翻一页、按q退出查看。
2. 用来查看命名的内置帮助信息: help  命令
   help  cd

#### Linux中的文件和目录操作的命令:

1. 查看当前所在目录: pwd
   pwd

2. 查看指定目录下所有的子目录和文件列表: ls  [指定目录]
   ls  /home       :ls查看当前目录下所有的子目录和文件列表
   ls   -l   /home :以列表形式显示
   ls  -a   /home :显示指定目录下所有的子目录和文件(包括虚拟的目录)
   ls  -al  /home :以列表形式显示指定目录下所有的子目录和文件(包括虚拟的目录)

3. 切换目录:cd目录名

   - 绝对目录:以盘符开始的目录叫绝对目录，从盘符开始查找目标目录

     cd  /opt/testDir

     - ~ : 当前用户的根目录。在任何目录下执行:cd ~，进入当前用户的根目录。

   - 相对目录:以目录名开始的目录叫相对目录，从当前目录开始查找目标目录

     cd  testDir

     - .. :当前目录的上一级目录，从的当前目录开始查找它的上一级目录。
     - .  :当前目录

4. 创建目录: mkdir  [选项]  目录名                                       

   - 绝对目录

   - 相对目录

     ```
     mkdir /opt/testDir/test1  //在/opt/testDir目录 下创建一一个 目录test1 (使用绝对目录)
     mkdir test2                       //在/opt/testDir目录 下创建一个目录test2 (使用相对目录) 
     mkdir -p /opt/testDir/test3/test4 //在/opt/testDir目 录下创建目录test3，并且在test3下创建test4(一次创建多级目录)
     ```

5. 删除一个空目录: rmdir  目录名

   ```
   - rmdir -p 操作: 递归删除多层级空目录
   ```

6. 创建一个或者多个空文件: touch  文件名列表(文件名之间用空格隔开)

   ```
   touch t1.txt
   touch t2.txt t3.txt t4.txt
   ```

7. 复制文件: cp  [选项]  source(源)  dest(目 标)

   ```
   cp t1.txt test2   //把t1.txt文件 复制到test2目录中
   cp -r test2 test5 //把test2目录复制到test5目录中(递归地复制目录)(没有-r只会复制test2这个目录里面为空)
   ```

8. 删除文件或者目录: rm  文件名或者目录名

   ```
   rm t1.txt        提示删除文件
   rm -f t2.txt    强制删除文件
   rm -r test2    提示递归删除目录
   rm -rf test5   强制递归删除目录
   ```

9. 移动目录或者文件: mv source(源)  dest(目标)

   ```
   mv  test.txt  test1
   mv  test1  test2
   mv  t3.txt  t3_new.txt    文件重命名
   ```

10. 查看文件内容(只读)：cat  [选项]  要查看的文件

    ```
    -n显示行号
    	cat  -n  opt/TestHelloWorld 					   查看文件
    	cat  -n  opt/TestHelloWorld  |  more		以cat指令打开文件并分页显示
    - 1、一次显示整个文件，具体命令是：cat  filename
    
    - 2、从键盘创建一个文件，具体命令是：cat  >  filename
    
    - 3、将几个文件合并为一个文件，具体命令是：cat  file1  file2 > file
    
    cat具体命令格式为 : cat [-AbeEnstTuv] [--help] [--version] fileName
    ```

11. more指令查看文件：more  -n  opt/TestHelloWorld 

    ```
    more指令是一个基于vi编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容。
    more指令中内置疗若干快捷键，详见操作说明
         - 空格键  ----  向下翻页
         - 回车  ----  向下翻一行
         - q  ----  代表立刻离开more 不再显示该文件内容
         - Ctri+F  ----  向下滚动一屏
         - Ctrl+B  ----  速回上一屏
         - =  ----  输出当前行的行号
         - f  ----  输出文件名和当前行的行号
    ```

12. less 与 more 类似：less  log2013.log

    ```
    j  ----  下一行
    k ----  上一行
    空格  ----  向下翻动一页
    ↑  ----  向上翻动一页
    ↓  ----  向下翻动一页
    q  ----  离开less程序
    /查找的内容  ----  查找  n -- 向下  N -- 向上查找
    
    less  log2013.log  log2014.log  浏览多个文件
    	输入 ：n后，切换到 log2014.log
    	输入 ：p 后，切换到log2013.log 
    ```

13. 显示指定文件头部内容: head  [参数]  文件 

    ```
    	-q 隐藏文件名
    	-v 显示文件名
    	-c<字节> 显示字节数
    	-n<行数> 显示的行数
    	
    head -n 5 head.txt		#显示前5行
    head -c 5 head.txt		#显示前5个字节
    ```

14. 显示指定文件末尾内容：tail  [必要参数]  [选择参数]  [文件]

    ```
      tail -n 5 log2014.log   #显示文件末尾5行的内容
    参数：  
      -f 循环读取
    
      -q 不显示处理信息
    
      -v 显示详细的处理信息
    
      -c<数目> 显示的字节数
    
      -n<行数> 显示行数
    
      -q, --quiet, --silent 从不输出给出文件名的首部 
    
      -s, --sleep-interval=S 与-f合用,表示在每次反复的间隔休眠S秒
    ```

15. echo: 输出系统变量或者常量的值到命令行终端。

    ```
    echo $JAVA_HOME
    echo $PATH
    JAVA_HOME=D:\DPES\Java\jdk1.8.0_101
    PATH= %JAVA_HOME%\bin; .......
    CLASSPATH=%JAVA_HOME%\lib; 
    ```

16. 把前一个查看命令的结果输出到指定的文件中:查看命令 >文件名

       - 如果目标文件不存在，则新建一个文件

       - 如果目标文件已存在，则把文件以前的内容覆盖

         ```
         ls  >  ret.txt
         ls  -al  >  ret.txt
         cat  ret.txt  >  t3_new.txt   文件内容的复制
         cat  t4.txt  >  t3_new.txt 
         ```

#### Linux中关于日期和时间的操作命令:

1. 查看或者设置系统的日期或者时间: date
   - date  查看系统当前的完整的日期和时间
   - date  +%Y  系统当前的年份
   - date  +%m 系统当前的月份
   - date  +%d  系统当前的日期
   - date '+%Y-%m-%d  %H:%M:%S'   按yy-MM-dd HH : mm:ss格式显示
   - date -S '2020-10-20 10:20:30'       设置当前的系统时间
2. 查看系统日历: cal
   cal                查看当前月份的口用
   cal   2020    查石指定年份的日历

#### Linux中关于搜索文件或者目录的命令: 

1. find命令: find   [搜索范围]  [搜索标准]  关键字
   				-name: 默认按名称搜索
        								-size: 按文件大小搜索
        								-user: 按文件的所有者搜索

   ```
   find *.txt					#搜索当前目录下，所有的.txt文件
   find *e*					#搜索当前目录下，所有名称中包含e的那些文件或者目录
   find /etc *.txt				#搜索/etc目录下所有.txt文件
   find /etc -size -5k 		#搜索/etc目录下所有小于5k的文件
   find /etc -size +5k 		#搜索/etc目录下所有大于5k的文件
   find /etc -size 5k	 		#搜索/etc目录下所有等于5k的文件
   find /etc -user zhangsan 	#搜索/etc目录下所有的所有者是zhangsan的文件和目录
   ```

2. locate:在整棵目录树中搜索文件或者目录，都是根据名称搜索，效率高。
   updatedb  ----  更新目录树的数据库
   locate  关键字  ----用之前先更新一次数据库
   updatedb
   locate  *. txt     查找所有.txt文件

3. 搜索过滤命令，在前一个搜素命令的结果中进行按名称进一步过滤:   搜素命令  Igrep  过滤条件
   查看命令  |grep  过滤条件

   -n  显示匹配行及行号。
   -i   忽略宇母大小写

   -ni  忽略大小写并显示行号

   管道符，"|",表示将前一个命令的处理结果输出传递给后面的命令处理。

   find  \*.txtIgrep  new            搜索当前目录下，所有名称包含new的.txt文件

   find  \*.txtIgrep  -i  new 	   搜索当前目录下，所有名称包含new的.txt文件,忽略大小写

   find  /etc  -size  -5k Igrep  firefox

#### Linux中有关压缩和解压的命令

1. 压缩或者解压单个文件:

   - gzip  文件名   ------   压缩单个文件  生成一个.gz的压缩包,并且会删除原来的文件

   - gunzip   文件名.gz   ------  解压单个文件  gz压缩包名:解压.gz压缩包，并且会把原来的.gz压缩包删除。

     gzip  TestHelloWorld.txt  	#目录下生成一个TestHelloWorld.txt.gz的文件

     gunzip  TestHelloWorld.txt.gz   #将.gz文件解压

2. 压缩(打包) 或者解压多个文件和目录: 

   - zip  目标压缩包名称(通常使用.zip压缩包)  文件或者目录列表

     - ```
       zip test.zip ret.txt t1.txt test2	#将ret.txt,t1.txt,test2打包为test.zip
       zip -dv cp.zip a.c		#删除cp.zip文件中的a.c文件
       ```

   - unzip  压缩包名(.zip) [ -d  解压目录名 ]   #将指定的.zip压缩包解压到当前目录(或者指定目录)。

     ```
     unzip test.zip -d test3				#解压到test3目录下
     unzip test.zip						#解压到当前目录下
     
     自行拓展============================================================================
     用zip -u 压缩包路径要存进的目录/文件名
     例1：我有个压缩包为/var/test.zip, 同时我有个文件为/var/nihao.txt
     	执行zip -u /var/test.zip /var/nihao.txt
     	，则你好.txt文件在压缩包中的路径仍为var/nihao.txt（在压缩包里创建了var文件夹，放了进去）
     例2：假设test.zip压缩包中有个文件夹名为Hi，我想把你好.txt放在Hi文件夹下
     	首先应该创建目录/var/Hi,然后把你好.txt放在Hi文件夹下，切换工作目录到/var，
     	执行zip -u /var/test.zip Hi/你好.txt即可
     ```

3. 压缩(打包)或者解压多个文件和目录: tar [选项]目 标压缩包名称(xxx.tar.gz)文件或者目录列表

   ```
   tar [选项] 压缩包名(xx.tar.gz) -C 解压目录名 #将指定的.tar.gz压缩包解压到当期目录(或者指定目录)
   ```

   - -c  ----  打包或者压缩  
   - -C  ----  指定解压到哪个目录
   - -v  ----  显示详细信息
   - -f   ----  指定压缩后的文件名
   - -z  ----  打包同时压缩
   - -x  ----  解压.tar.gz文件

   ```
   tar -zcvf xxx.tar.gz 文件或者目录列表
   tar -zcvf mytar.tar.gz mytest.zip ret.txt t1.txt test2
   tar -ZXVf xxx.tar.gz -C 解压目录名
   tar -ZXvf mytar.tar.gz -C /opt/testDir/test5
   ```

#### 文件或者目录与组:

1. 文件或者目录与组基本介绍:

   - 在Linux中,每一个用户都至少属于一个组，用户不能独立于组存在，一个用户可以属于多个组。
   - 在Linux中，每一个文件或者目录也必须属于一个组，而且只能属于一个组，默认情况下，文件所有者所属的主组就是文件所属的组;
   - 文件或者目录通过组来控制哪些用户可以对它进行哪些操作，即文件或者目录的访问权限;
     - 在文件或者目录看来，Linux系统中所有的用户分为三类:
       - 所有者:默认情况下，文件或者目录的所有者都是创建者，可以修改
       - 同组用户:跟文件或者目录属于同一一个组的用户
       - 其它组用户:既不是文件或者目录的所有者，也不是同组用户.

2. 查看文件的所有者和所在的组:ls  -l

3. 修改文件或目录的所有者: chown  新的所有者  文件名

   - -R : 处理指定目录以及其子目录下的所有文件

   ```
   chown 新的所有者:新的组文件名
   chown root /var/run/httpd.pid	#把/var/run/httpd.pid 的所有者设置root
   chown zhangsan t1.txt			##把t1.txt 的所有者设置zhangsan
   chown -R zhangsan test3			
   chown zhangsan:dev t4.txt		#将t4.txt所有者和所在组分别改为 zhangsan 和 dev
   chown zhangsan:dev test2
   chown -R zhangsan:dev test2 	#递归修改目录的所有者和所在的组
   ```

4. 修改文件或者目录的所在组: chgrp  新的组  文件名或者目录名

   chgrp  dev  t2.txt			将t2.txt的组改为dev
   chgrp  -R  dev  test3

#### Linux中文件或者目录的权限管理:

1. 准备工作:

   - 一个用户至少属于一个组，也可以属于多个组;
   - 一个文件或者目录也必须属于一个组，并且只能属于一个组;
   - 在一个文件或者目录看来，Linux 系统中所有的用户可以分为三类:
     - 所有者:
     - 同组用户:
     - 其它组用户:

2. 文件或者目录的三种权限:

   - 在Linux中，任何文件或者目录都有三种权限:

     - 读(Read)
     - 写(Write)
     - 执行(Execute)

   - 对于文件而言:

     - 读:可以读取、查看文件的内容，比如: cat、more、less、head、tail等
     - 写:可以修改文件的内容，比如: vi 或者vim等
     - 执行:如果该文件是可执行文件(.sh)，可以直接运行，比如:  . /xxx.sh

   - 对目录而言:

     - 读:可以读取、查看目录下边的内容，比如: ls等

     - 写:可以修改目录中的内容，创建子目录、删除子目录、创建文件、删除文件、重名文件或者目录

     - 执行:可以进入该目录，比如: cd等

       ```
       ①-rw-r--r--. ②1 ③root ④root  ⑤132 ⑥2月  17 21:55 ⑦TestHelloWorld2.txt
       ①-rw-r--r--.		第一位表示文件类型:	-普通文件	l软连接	b块文件，硬盘
       				  				  d目录	   c字符设备（鼠标、键盘）
       -(文件类型) rw-(文件所持有者的权限) r--(同组成员权限) r--(其他组成员的权限)
       ②如果是文件表示硬链接的数如果是目录则表示该目录的子目录个数
       ③用户
       ④组
       ⑤文件的大小如果是目录则为4096
       ⑥文件最后的修改时间
       ⑦文件名
       ```

3. 修改权限：chmod

   - 第一种方式：

     ```
     u--所有者   g--所有组   o--其他人   a--所有人(u,g,o的总和)
     chmod u=rw,g=rx,o=x 文件或目录名
     chmod o+w 文件或目录名
     chmod a-x 文件或目录名
     ```

   - 第二种方式：通过数字变更权限

     ```
     规则: r=4 w=2 x=1  rwx=4+2+1=7
     chmod u=rwx,g=rx,o=x 文件或目录名   相当于   chmod 751 文件或目录名
     ```

#### Linux中的网络配置

- Linux中的网络管理:

  - 在Linux的配置文件: vi /etc/sysconfig/network-scripts/ ifcfg-ens33

    ```
    BOOTPROTO = "static"
    ONBOOT = "yes"
    
    IPADDR = 192.168.11.128		#根据需要自行更改
    GATEWAY = 192.168.11.2
    DNS1 = 192.168.11.2    #DNS不加1网络是通的，但是不能解析域名
    
    重启Linux:
    reboot
    ```

- 查看网络连接状态：netstat  -tnlp

  语法：#netstat -tnlp

  - -t：表示只列出tcp协议的连接
  - -n：表示将地址local adress 的地址组合转换成ip地址，将协议转化成端口号来表示
  - -l：表示过滤出“state（状态）”列中其值为LISTEN（监听）的连接。
  - -p：表示显示发起连接的进程的PID和进程的名称

#### Linux中的进程管理:

- 线程:一个程序的线路

- 进程:一个程序的执行，一个进程占用一个端口。

  - 查看正在运行的进程: ps

    ```
    ps //只会显示应用进程
    ps -au //显示较详细的资讯
    ps -e //显示所有进程.
    ps -ef //以全格式的形式显示所有进程
    ps -eflgrep mysql	//用于查看Linux系统中某一些软件或者应用是否处于启
    ```

- 动状态关闭进程:

  - 使用ps命令查看进程的PID

  - 使用命令kill -9 PID

    ```
    ps 				查看
    kill 9 PID		杀死
    ```

  - 与kill命令作用相似但是比kill更好用的杀死进程的命令：killall

    语法：#killall 进程名

#### Linux中服务管理:

1. 服务介绍:服务是支持Linux运行的一些必要程序，本质上也是进程，叫守护进程。
2. 操作服务: systemctl [start | stop | restart | reload | status | enable] 服务名称
   - systemctl status firewalld 查看 防火墙运行状态
   - systemctl stop firewalld 关闭防火墙
   - systemctl start firetalld 开启防火墙
   - systemctl enable firewalld 设置防火墙开机启动
   - 老版的Linux或者有些发行版本的Linux，操作服务使用service命令。

#### Linux中软件包的管理:

软件安装包: RPM:一 种Linux的软件包的打包和安装工具，它操作的软件包都是.rpm结尾。

1. 使用RPM: rpm命令 。

   - 查看当前系统中已经安装的rpm软件包: rpm -qa | grep firefox

   - 卸载rpm软件包: rpm -e firefox

   - 安装rpm包: rpm -ivh XX8. rpm

     - -i  ----  安装

     - -v  ----  显示详细信息

     - -h  ----  显示进度条

       ```
       cp firefox-45.4.0-1.e17.centos.x86_64.rpm /opt
       ```

2. YUM包管理:是一种基于RPM的软件包管理工具，它能够从指定服务器上自动下载RPM包并且自动安装，可以自动处理软件包之间的依赖关系

   - 查看当前系统中已经安装的rpm软件包: yum list installedIgrep firefox
   - 卸载rpm软件包|: yum remove firefox.x86_64
   - 安装rpm包: yum install firefox

#### [搭建JAVAEE开发环境](.\超链接文件\搭建JAVAEE开发环境.pdf)

#### 进阶

1. 查看磁盘空间

   ```
   df -h
   ```

2. 查看内存使用

   ```
   free -m
   ```

3. 统计文件内容信息（行数 单词数 字节数）语法: wc -lwc需要统计的文件路径，

   ```
   wc -l
   l:表示lines 适用。
   w:表示words主要是对英文适用。
   c:表示bytes
   ```

   

