Oracle DB启动
===

##Oracle DB启动，共三个阶段：**nomount**, **mount**, **open**。
---

### * NOMOUNT

在创建数据库期间、重新创建控制文件期间，或执行某些备份和恢复方案期间，通常只在NOMOUNT模式下启动实例。
 
启动实例过程包括执行以下任务：

按以下顺序搜索$ORACLE_HOME/dbs中具有特定名称的文件：
1. 搜索spfile<SID>.ora。
2. 如果未找到spfile<SID>.ora，则搜索spfile.ora。
3. 如果未找到spfile.ora，则搜索init<SID>.ora。

这是包含实例初始化参数的文件。使用STARTUP指定PFILE参数可覆盖默认行为。

* 分配SGA
* 启动后台进程
* 打开alert_<SID>.log文件和跟踪文件

注：SID是用于标识实例的系统ID（例如ORCL）。

### * MOUNT

数据库装载过程包括执行以下任务：

* 将数据库与以前启动的实例关联
* 定位并打开参数文件中指定的控制文件
* 通过读取控制文件来获取数据文件和联机重做日志文件的名称和状态（但是，此时不会执行检查来验证是否存在数据文件和联机重做日志文件）。
 
要执行特定的维护操作，则启动实例，然后装载数据库，但不打开该数据库。
例如，在执行以下任务期间必须装载数据库，但不得打开数据库：

* 重命名数据文件（打开数据库时可重命名脱机表空间的数据文件）。
* 启用和禁用联机重做日志文件归档选项
* 执行完整的数据库恢复
 
注：即使发出了OPEN请求，数据库仍可能处于MOUNT模式下。这是因为可能需要以某种方式恢复数据库。如果在MOUNT状态下执行恢复，将打开重做日志进行读取，并打开数据文件读取需要恢复的块，以及在恢复期间根据需要写入块。

### * OPEN
数据库操作正常意味着实例已启动、数据库已装载且已打开。在数据库操作正常时，任何有效用户都可连接到数据库，而且可执行典型数据访问操作。
打开数据库过程包括执行以下任务：

* 打开数据文件
* 打开联机重做日志文件
如果尝试打开数据库时任一数据文件或联机重做日志文件不存在，则Oracle 服务器返回错误。
 
在最后这个阶段，Oracle 服务器会验证是否可以打开所有数据文件和联机重做日志文件，还会检查数据库的一致性。如有必要，系统监视器(SMON) 后台进程将启动实例恢复。可以在受限模式下启动数据库实例，以便只让有管理权限的用户使用该实例。要在受限模式下启动实例，可在“Advanced Startup Options（高级启动选项）”页上选择“Restrict access to database（限制对数据库的访问）”选项。
或者在启动Open模式时，添加restrict关键字：startup restrict，
设置或取消受限状态：alter system enable\disable restricted session;