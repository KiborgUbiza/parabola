Чтобы настроить GRUB на загрузку Windows в системе с двумя дисками (один с Windows, другой с Arch Linux, каждый с собственным разделом EFI), выполните следующие шаги:

  

1. Убедитесь, что обе системы используют UEFI

• Проверка для Arch Linux:

Выполните команду:

  

ls /sys/firmware/efi

  

Если папка существует, значит система работает в UEFI.

  

• Проверка для Windows:

В Windows откройте командную строку и выполните:

  

bcdedit

  

Если путь к загрузчику начинается с \EFI\Microsoft\Boot\bootmgfw.efi, значит Windows установлена в UEFI.

  

2. Установите GRUB и дополнительные утилиты

  

В Arch Linux установите GRUB и необходимые утилиты:

  

sudo pacman -S grub efibootmgr os-prober

  

Убедитесь, что модуль os-prober будет использоваться для обнаружения других ОС:

1. Откройте файл /etc/default/grub:

  

sudo nano /etc/default/grub

  

  

2. Убедитесь, что нет строки:

  

GRUB_DISABLE_OS_PROBER=true

  

Если она есть, закомментируйте её (добавьте # в начале строки) или удалите.

  

3. Смонтируйте разделы EFI

1. Определите разделы EFI для Windows и Linux:

  

sudo fdisk -l

  

Пример вывода:

  

Device        Start       End   Sectors  Size Type

/dev/sda1     2048    534527    532480  260M EFI System

/dev/sdb1     2048    534527    532480  260M EFI System

  

Допустим:

• /dev/sda1 — EFI-раздел для Arch Linux.

• /dev/sdb1 — EFI-раздел для Windows.

  

2. Смонтируйте EFI-раздел Arch Linux:

  

sudo mount /dev/sda1 /boot

  

  

3. (Необязательно) Смонтируйте EFI-раздел Windows для проверки:

  

sudo mount /dev/sdb1 /mnt

ls /mnt/EFI/Microsoft/Boot/bootmgfw.efi

  

Если файл существует, это правильный раздел.

  

4. Установите GRUB

  

Установите GRUB на диск, где находится Linux:

  

sudo grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB

  

5. Проверьте, видит ли os-prober Windows

1. Запустите os-prober для проверки:

  

sudo os-prober

  

Если Windows обнаружен, вы увидите путь к загрузчику, например:

  

/dev/sdb1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi

  

  

2. Если Windows обнаружен, обновите конфигурацию GRUB:

  

sudo grub-mkconfig -o /boot/grub/grub.cfg

  

В выводе должно появиться что-то вроде:

  

Found Windows Boot Manager on /dev/sdb1

  

6. Если Windows не обнаружен автоматически

  

Если os-prober не обнаружил Windows, добавьте запись вручную.

1. Откройте файл /etc/grub.d/40_custom:

  

sudo nano /etc/grub.d/40_custom

  

  

2. Добавьте запись для Windows:

  

menuentry "Windows 10" {

    insmod part_gpt

    insmod fat

    set root=(hd1,gpt1)     # Замените на EFI-раздел Windows

    chainloader /EFI/Microsoft/Boot/bootmgfw.efi

}

  

  

3. Сохраните изменения и обновите GRUB:

  

sudo grub-mkconfig -o /boot/grub/grub.cfg

  

7. Перезагрузка и выбор системы

1. Перезагрузите компьютер.

2. Убедитесь, что в меню GRUB появилась запись для Windows.

  

Пример конфигурации

• Linux EFI: /dev/sda1, монтируется в /boot.

• Windows EFI: /dev/sdb1, монтируется временно в /mnt.

• В GRUB:

• Linux: определяется автоматически.

• Windows: добавляется автоматически или вручную через /etc/grub.d/40_custom.

  

Если что-то пойдет не так, напишите, разберем вашу конфигурацию более детально.
