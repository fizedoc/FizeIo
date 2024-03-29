===============
目录操作类
===============


+-------------+----------+
|属性         |值        |
+=============+==========+
|命名空间     |fize\\io  |
+-------------+----------+
|类名         |Directory |
+-------------+----------+


:方法:


+---------------------+-------------------------------------------------------------------------+
|方法名               |说明                                                                     |
+=====================+=========================================================================+
|`__construct()`_     |构造函数                                                                 |
+---------------------+-------------------------------------------------------------------------+
|`__destruct()`_      |析构函数                                                                 |
+---------------------+-------------------------------------------------------------------------+
|`dir()`_             |获取当前的Directory对象                                                  |
+---------------------+-------------------------------------------------------------------------+
|`mk()`_              |创建目录                                                                 |
+---------------------+-------------------------------------------------------------------------+
|`open()`_            |打开指定目录                                                             |
+---------------------+-------------------------------------------------------------------------+
|`close()`_           |关闭当前目录                                                             |
+---------------------+-------------------------------------------------------------------------+
|`ch()`_              |改变当前目录                                                             |
+---------------------+-------------------------------------------------------------------------+
|`chroot()`_          |改变根目录                                                               |
+---------------------+-------------------------------------------------------------------------+
|`getcwd()`_          |取得当前工作目录                                                         |
+---------------------+-------------------------------------------------------------------------+
|`read()`_            |遍历当前目录的文件条目                                                   |
+---------------------+-------------------------------------------------------------------------+
|`rewind()`_          |将当前目录流重置到目录的开头。                                           |
+---------------------+-------------------------------------------------------------------------+
|`scan()`_            |列出指定路径中的文件和目录 (含.和..)                                     |
+---------------------+-------------------------------------------------------------------------+
|`createFile()`_      |创建一个空文件                                                           |
+---------------------+-------------------------------------------------------------------------+
|`createDirectory()`_ |新建目录                                                                 |
+---------------------+-------------------------------------------------------------------------+
|`deleteFile()`_      |删除指定文件                                                             |
+---------------------+-------------------------------------------------------------------------+
|`deleteDirectory()`_ |删除指定文件夹                                                           |
+---------------------+-------------------------------------------------------------------------+
|`clear()`_           |清理当前工作文件夹，即删除里面的所有文件及文件夹                         |
+---------------------+-------------------------------------------------------------------------+
|`isDir()`_           |判断给定文件名是否是一个目录                                             |
+---------------------+-------------------------------------------------------------------------+
|`glob()`_            |寻找与模式匹配的文件路径                                                 |
+---------------------+-------------------------------------------------------------------------+
|`diskFreeSpace()`_   |返回目录中的可用空间                                                     |
+---------------------+-------------------------------------------------------------------------+
|`diskTotalSpace()`_  |返回一个目录的磁盘总大小                                                 |
+---------------------+-------------------------------------------------------------------------+
|`realpath()`_        |返回规范化的绝对路径名                                                   |
+---------------------+-------------------------------------------------------------------------+
|`tempnam()`_         |在当前工作文件夹建立一个具有唯一文件名的文件                             |
+---------------------+-------------------------------------------------------------------------+


方法
======
__construct()
-------------
构造函数

.. code-block:: php

  public function __construct (
      string $path,
      bool $auto_build = false
  )


:参数:
  +-----------+----------------------------------+
  |名称       |说明                              |
  +===========+==================================+
  |path       |指定目录路径                      |
  +-----------+----------------------------------+
  |auto_build |指定的路径不存在时创建            |
  +-----------+----------------------------------+
  
  


__destruct()
------------
析构函数

.. code-block:: php

  public function __destruct ()



dir()
-----
获取当前的Directory对象

.. code-block:: php

  public static function dir (
      string $path
  ) : \Directory


:参数:
  +-------+-------------------+
  |名称   |说明               |
  +=======+===================+
  |path   |指定目录路径       |
  +-------+-------------------+
  
  


mk()
----
创建目录

.. code-block:: php

  public static function mk (
      string $path,
      int $mode = 511,
      bool $recursive = true
  ) : bool


:参数:
  +----------+-------------------------------------------------+
  |名称      |说明                                             |
  +==========+=================================================+
  |path      |要创建的目录，已存在则不进行处理                 |
  +----------+-------------------------------------------------+
  |mode      |权限                                             |
  +----------+-------------------------------------------------+
  |recursive |是否可递归创建多层目录                           |
  +----------+-------------------------------------------------+
  
  


open()
------
打开指定目录

.. code-block:: php

  public function open (
      string $path
  )


:参数:
  +-------+-------------+
  |名称   |说明         |
  +=======+=============+
  |path   |指定目录     |
  +-------+-------------+
  
  


close()
-------
关闭当前目录

.. code-block:: php

  public function close ()



ch()
----
改变当前目录

.. code-block:: php

  public static function ch (
      string $path
  ) : bool


:参数:
  +-------+-------------+
  |名称   |说明         |
  +=======+=============+
  |path   |指定目录     |
  +-------+-------------+
  
  

:返回值:
  如果指定目录不存在也返回false


chroot()
--------
改变根目录

.. code-block:: php

  public static function chroot (
      string $path
  ) : bool


:参数:
  +-------+-------------+
  |名称   |说明         |
  +=======+=============+
  |path   |指定目录     |
  +-------+-------------+
  
  


::

    本函数仅在系统支持且运行于 CLI，CGI 或嵌入 SAPI 版本时才能正确工作。
    此外本函数还需要 root 权限。
    此函数未在 Windows 平台下实现，故也返回false


getcwd()
--------
取得当前工作目录

.. code-block:: php

  public static function getcwd () : string



read()
------
遍历当前目录的文件条目

.. code-block:: php

  public function read (
      callable $func,
      bool $filter_base = false
  )


:参数:
  +------------+-------------------+
  |名称        |说明               |
  +============+===================+
  |func        |遍历函数           |
  +------------+-------------------+
  |filter_base |是否剔除.和..      |
  +------------+-------------------+
  
  


::

    参数 `$func` :
    函数参数($file); $file : 条目名称


rewind()
--------
将当前目录流重置到目录的开头。

.. code-block:: php

  public function rewind ()



scan()
------
列出指定路径中的文件和目录 (含.和..)

.. code-block:: php

  public static function scan (
      string $path,
      int $sorting_order = 0
  ) : array


:参数:
  +--------------+-------+
  |名称          |说明   |
  +==============+=======+
  |path          |路径   |
  +--------------+-------+
  |sorting_order |排序   |
  +--------------+-------+
  
  


createFile()
------------
创建一个空文件

.. code-block:: php

  public static function createFile (
      string $name,
      bool $recursive = false
  ) : bool


:参数:
  +----------+----------------------------------+
  |名称      |说明                              |
  +==========+==================================+
  |name      |文件路径                          |
  +----------+----------------------------------+
  |recursive |是否可递归创建多层目录            |
  +----------+----------------------------------+
  
  


createDirectory()
-----------------
新建目录

.. code-block:: php

  public static function createDirectory (
      string $name,
      int $mode = 511,
      bool $recursive = false
  ) : bool


:参数:
  +----------+----------------------------------+
  |名称      |说明                              |
  +==========+==================================+
  |name      |新建目录名                        |
  +----------+----------------------------------+
  |mode      |设置访问权                        |
  +----------+----------------------------------+
  |recursive |是否可递归创建多层目录            |
  +----------+----------------------------------+
  
  

:返回值:
  已有该目录则也返回true


deleteFile()
------------
删除指定文件

.. code-block:: php

  public static function deleteFile (
      string $name
  ) : bool


:参数:
  +-------+-------------+
  |名称   |说明         |
  +=======+=============+
  |name   |文件路径     |
  +-------+-------------+
  
  

:返回值:
  没有该文件则也返回true


::

    虽然该方法也可以用来删除文件夹，但不建议如此使用


deleteDirectory()
-----------------
删除指定文件夹

.. code-block:: php

  public static function deleteDirectory (
      string $name,
      bool $force = false
  ) : bool


:参数:
  +-------+--------------------------------------------------+
  |名称   |说明                                              |
  +=======+==================================================+
  |name   |要删除的目录名， 可以指定多级目录                 |
  +-------+--------------------------------------------------+
  |force  |如果目录不为空时是否强制删除                      |
  +-------+--------------------------------------------------+
  
  


clear()
-------
清理当前工作文件夹，即删除里面的所有文件及文件夹

.. code-block:: php

  public static function clear () : bool



isDir()
-------
判断给定文件名是否是一个目录

.. code-block:: php

  public static function isDir (
      string $path
  ) : bool


:参数:
  +-------+-------------+
  |名称   |说明         |
  +=======+=============+
  |path   |指定目录     |
  +-------+-------------+
  
  


glob()
------
寻找与模式匹配的文件路径

.. code-block:: php

  public static function glob (
      string $pattern,
      int $flags = null
  ) : array


:参数:
  +--------+-------------+
  |名称    |说明         |
  +========+=============+
  |pattern |匹配模式     |
  +--------+-------------+
  |flags   |有效标识     |
  +--------+-------------+
  
  


diskFreeSpace()
---------------
返回目录中的可用空间

.. code-block:: php

  public static function diskFreeSpace (
      string $directory
  ) : float


:参数:
  +----------+----------------------+
  |名称      |说明                  |
  +==========+======================+
  |directory |指定目录或盘符        |
  +----------+----------------------+
  
  

:返回值:
  可用的字节数，失败时返回false


diskTotalSpace()
----------------
返回一个目录的磁盘总大小

.. code-block:: php

  public static function diskTotalSpace (
      string $directory
  ) : float


:参数:
  +----------+----------------------+
  |名称      |说明                  |
  +==========+======================+
  |directory |指定目录或盘符        |
  +----------+----------------------+
  
  

:返回值:
  字节数，失败时返回false


realpath()
----------
返回规范化的绝对路径名

.. code-block:: php

  public function realpath () : string



tempnam()
---------
在当前工作文件夹建立一个具有唯一文件名的文件

.. code-block:: php

  public static function tempnam (
      string $prefix = ""
  ) : string


:参数:
  +-------+----------------------------+
  |名称   |说明                        |
  +=======+============================+
  |prefix |产生临时文件的前缀          |
  +-------+----------------------------+
  
  

:返回值:
  返回其文件名


