# repair_efi_in_dual_boot

最近想给电脑装个Ubuntu双系统，结果在安装的过程中把整个efi分区给删掉并被Linux的efi分区覆盖了

最初是发现启动Linux无法进入grub。 于是修改 /etc/default/grub。 修改成功后发现进入grub后没有windows选项（此时还没有意识到问题的严重性）。

