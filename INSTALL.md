# Paint 11 — install & "open with" setup

## 1. Get it running (Arch / Python 3.14 fix)

The font crash you hit is because pip's pygame 2.6.1 has no working
Python 3.14 build. Use pygame-ce inside a venv:

    # clean up the broken pip files that blocked pacman
    sudo rm -rf /usr/lib/python3.14/site-packages/pygame \
                /usr/lib/python3.14/site-packages/pygame-2.6.1.dist-info \
                /usr/include/python3.14/pygame

    cd ~
    python -m venv venv
    source venv/bin/activate
    pip install pygame-ce
    python paint11.py            # blank canvas
    python paint11.py photo.png  # open an image directly

If the font module STILL errors on 3.14, run it under Python 3.13:

    sudo pacman -S python313
    python3.13 -m venv venv313
    source venv313/bin/activate
    pip install pygame-ce
    python paint11.py

## 2. What's new in this version
- Drag an image file onto the window  -> it opens.
- Ctrl+O now shows a real file picker (zenity / kdialog / tkinter).
- Ctrl+S / Ctrl+Shift+S show a real save dialog.
- `python paint11.py somefile.png` opens that file on launch.

## 3. Make it your default image app

Edit the Exec line in paint11.desktop so it points at how you launch it.
If you used a venv, point Exec at the venv's python, e.g.:

    Exec=/home/k/venv/bin/python /home/k/paint11.py %f

Then:

    cp paint11.desktop ~/.local/share/applications/
    update-desktop-database ~/.local/share/applications

Set as default for PNGs (repeat per type you want):

    xdg-mime default paint11.desktop image/png
    xdg-mime default paint11.desktop image/jpeg

Now double-clicking an image (or "Open With") launches Paint 11 with it.
