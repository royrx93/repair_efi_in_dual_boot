# repair_efi_in_dual_boot

最近想给电脑装个Ubuntu双系统，结果在安装的过程中把整个efi分区给删掉并被Linux的efi分区覆盖了

最初是发现启动Linux无法进入grub。 于是修改 /etc/default/grub。 修改成功后发现进入grub后没有windows选项（此时还没有意识到问题的严重性）。

而后采取

1. 重装Linux， 未果。（意识到是efi文件的问题，开始了解efi原理）

2. 使用Linux的boot-repair修复，未果。 显示的错误是 Windows可能处于legacy模式，需要主板开启uefi&legacy兼容模式；但我的主板(Rog B550i)一直是UEFI&Legacy兼容模式.

3. 使用 tripleZ's blog 中修复的方法，但是无法成功分配C盘 盘符， 未果。

4. 使用傲梅分区助手恢复分区， 但也没有找到丢失分区(a. 完全搜索时间太长没有进行； b. 并么有丢失分区)

5. 此时发现 另一块仓库盘中的分区被分配为了C盘！！！(在安装Linux之前曾经修改过这块的分区)

6. 采取tripleZ的方法成功用diskpart分配C盘盘符，但无法给efi分区分配盘符

7. 用傲梅分区助手给efi分区盘符成功！！！

8. 命令 bcdboot 复制win10 efi分区文件.(此时已经可以在bios中看到Windows Boot Manager，但在grub中还没Windows选项)

9. 在Linux中 update-grub

10. 完成！ 此时grub终于有Windows选项，并且可以顺利启动Windows！！！ 
