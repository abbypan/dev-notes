3ds
########

3ds hack: https://stray-soul.com/

gm9/out backup: https://stray-soul.com/finalizing-setup.html

install cia to sdcard directly
==============================

3ds custom install: https://stray-soul.com/ci.html

export: boot9.bin, movable.sed

seeddb.bin: https://github.com/ihaveamac/3DS-rom-tools/wiki/SeedDB-list

3dsconv (3ds -> cia)
====================

3ds -> cia

3dsconv.exe: https://github.com/ihaveamac/3dsconv

::

   3dsconv --boot9=boot9.bin [3ds_file]

saves (3ds -> citra, citra -> 3ds)
==================================

use `jksm <https://github.com/J-D-K/JKSM/releases>`__ or
`checkpoint <https://www.gamebrew.org/wiki/Checkpoint_3DS>`__,
export/restore the ``*.fsd`` file

jksm path: sdcard:/JKSV/Saves/…

checkpoint path: sdcard:/3DS/checkpoint/saves/…

citra windows path (windows user xxx, game yyy):

::

   C:\users\xxx\AppData\Roaming\Citra\sdmc\Nintendo 3DS\000...000\000...000\title\00040000\00xxxx\data\000xxx\yyy.fsd

citra
==========

小马模拟器的citra存档路径

\PonyEmu\System\citra\sdmc

需要手动拷，直接点备份不成功
