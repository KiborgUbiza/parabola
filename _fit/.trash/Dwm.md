 [[карта патчей]]
 [[Все патчи]]

 Basic
=====

[Shift]+[Mod]+[Enter]   - launch terminal.

[Mod]+[b]               - show/hide bar.
[Mod]+[p]               - dmenu for running programs like the x-www-browser.
[Mod]+[Enter]           - push acive window from stack to master, or pulls last used window from stack onto master.

[Mod] + [j / k]         - focus on next/previous window in current tag.
[Mod] + [h / l]         - increases / decreases master size.

Navigation
==========

[Mod]+[2]               - moves your focus to tag 2.
[Shift]+[Mod]+[2]       - move active window to the 2 tag.

[Mod] + [i / d]         - increases / decreases number of windows on master
[Mod] + [, / .]         - move focus between screens (multi monitor setup)
[Shift]+[Mod]+[, / .]   - move active window to different screen.

[Mod]+[0]               - view all windows on screen.
[Shift]+[Mod]+[0]       - make focused window appear on all tags.
[Shift]+[Mod]+[c]       - kill active window.
[Shift]+[Mod]+[q]       - quit dwm cleanly.

Layout
======

[Mod]+[t]               - tiled mode. []=
[Mod]+[f]               - floating mode. ><>
[Mod]+[m]               - monocle mode. [M] (single window fullscreen)

Floating
========

[Mod]+[R M B]           - to resize the floating window.
[Mod]+[L M B]           - to move the floating window around.
[Mod]+[Space]           - toggles to the previous layout mode.
[Mod]+[Shift]+[Space]   - to make an individual window float.
[Mod]+[M M B]           - to make an individual window un-float.

В dwm расположение окон зависит от выбранной раскладки. Вы можете изменять расположение окон, выбирая разные раскладки, перемещая окна между ними или изменяя их положение вручную. Вот как это сделать:

  

1. Использование стандартных раскладок

  

В dwm по умолчанию есть три раскладки:

1. Tile (плитка): Окна располагаются в виде основной области (master) и стековой области (stack). Основное окно находится слева, остальные окна — справа.

2. Monocle (одно окно): Одно окно занимает весь экран.

3. Floating (плавающие окна): Окна можно перемещать и изменять их размер вручную.

  

Горячие клавиши для изменения раскладок:

• Mod+T: Переключиться на плиточную раскладку.

• Mod+M: Переключиться на раскладку с одним окном (monocle).

• Mod+Shift+Space: Переключиться на плавающую раскладку.

  

2. Перемещение окон между основным и стеком

• Сделать окно основным (master):

Нажмите Mod+Enter, чтобы переместить активное окно в область master.

• Перемещение окон в стеке:

Используйте Mod+J или Mod+K для переключения между окнами в стеке.

  

3. Плавающее управление окнами

  

Если окно в плавающем режиме, его можно перемещать или изменять размеры вручную:

• Перемещение окна: Зажмите Mod и перетащите окно левой кнопкой мыши.

• Изменение размера: Зажмите Mod и перетащите окно правой кнопкой мыши.

  

Чтобы переключить окно в плавающее состояние или обратно, нажмите:

• Mod+Shift+Space.

  

4. Изменение размера master-области

  

В плиточной раскладке можно изменять размер master-области:

• Увеличить область master: Mod+L.

• Уменьшить область master: Mod+H.

  

5. Перемещение окон между тегами

  

Вы можете перемещать окна между тегами:

• Переключить окно на другой тег:

Зажмите Mod+Shift+{1-9} (цифра соответствует тегу), чтобы переместить активное окно на другой тег.

• Переключиться на другой тег:

Нажмите Mod+{1-9}.At