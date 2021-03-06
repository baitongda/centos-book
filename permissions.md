# 权限

macOS 与 Linux 都属于 Unix 类型的操作系统，所以它们的文件与目录的权限的概念是一样的。

## 三个动作

系统上的一个用户，对某个文件或目录能做的有三个动作：读取，写入，执行。这三个动作也可以看成是三个权限，用户可以读取文件里的内容，我们就说他对这个文件拥有读取的权限。如果用户可以在某个目录的下面创建新的文件，我们就可以说这个用户对于这个目录来说拥有写入的权限。

这三个权限用字母表示：

* r：read（读取）
* w：write（写入）
* x：excute（执行）

## 三种人

对于文件与目录来说，有三种人：**拥有者（owner），用户组（group），其它人（others）**。你可以分别设置文件与目录对于这三种人的权限。文件与目录会属于某个人（owner：拥有者）还有某个用户组（group），一个用户创建了文件或目录以后这些属性就被定义好了。比如 wanghao 创建了一个文件，那这个文件的拥有者就会是 wanghao，文件所属的用户组就是这个用户的主群组。

## 权限的表示

在列出目录内容的时候，如果使用 -l 选项，就会显示内容的权限。用 wanghao 这个用户的身份去创建一个文件：

```
su wanghao
cd ~
touch hello.txt
```

列出：

```
ls -l
```

返回：

```
-rw-rw-r--. 1 wanghao wanghao 0 May 16 09:50 hello.txt
```

`-rw-rw-r--` 就表示 hello.txt 这个文件对于文件的拥有者，用户组还有其它人的权限。第一个 `-` 的位置表示是否是目录，如果内容是目录这个地方应该是 `d` 。

后面三位指的是拥有者的权限，`rw-`，表示读取与写入权限，最后一位是执行权限，这里是个 `-` ，表示没有执行权限。

再往后三位表示的是用户组的权限，`rw-`，表示读取与写入权限，最后一位是执行权限，这里是个 `-` ，表示没有执行权限。

最后三位表示的是其它人对这个文件的权限，`r--`，表示读取权限，第二位是写入权限，这里是 `-` ，表示没有写入权限。最后一位是执行权限，这里也是 `-`，表示其它人对于这个文件来说也没有执行权限。

### 数字表示的权限

权限可以使用数字表示：

* r：4
* w：2
* x：1

也就是如果一种人，比如文件的拥有者，他的权限可以用数字 7 表示的话，那他的权限就是 4 + 2 + 1，也就是 r + w + x，也就是 **读取 + 写入 + 执行**，也就是拥有者拥有所有的权限。

再比如，一个文件对于其它人的权限如果用数字  4 表示的话，那其它人的权限就是 r ，也就是读取，也就是其它人只有读取文件的权限，因为表示读取权限的数字是 4 。

* 7：r + w + x，表示所有权限
* 6：r + w，表示读取与写入权限
* 4：r，表示读取权限

## 权限的修改

文件与目录为三种人准备的这三组权限，可以通过 chmod（change mode） 命令修改。

## 所有权的修改

修改目录或文件的所有权，也就是拥有者与所属用户组，用的是 chown（change owner） 命令。



