Mac如何读写NTFS格式的磁盘：

流程简介

挂载上你的NTFS硬盘，查看硬盘名称
编辑/etc/fstab文件，使其支持NTFS写入
将/Volumes中的NTFS磁盘快捷方式到Finder
详细流程

插上硬盘后，查看你的硬盘名称，这里假设名称是AngleDisk，牢记之（你的可不是这个呀！！）

打开Applications的Terminal, 你也可以直接spotlight输入terminal打开

在终端输入sudo nano /etc/fstab 敲击回车

现在你看到了一个编辑界面，输入LABEL=AngleDisk none ntfs rw,auto,nobrowse后，敲击回车，再Ctrl+X，再敲击Y，再敲击回车

此时，退出你的移动硬盘，再重新插入，你会发现磁盘没有显示再桌面或是Finder之前出现的地方，别慌

打开Finder，Command+Shift+G，输入框中输入/Volumes，回车，你就可以看到你的磁盘啦！是可以读写的哟，Enjoy

方便起见，你可以直接把磁盘拖到Finder侧边栏中，这样下次使用就不用进入到/Volumes目录打开了