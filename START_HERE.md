# Paint 11 — how to start it

## First time only

Open a terminal and paste these, one block at a time.

1) Clean up the broken install:

    sudo rm -rf /usr/lib/python3.14/site-packages/pygame \
                /usr/lib/python3.14/site-packages/pygame-2.6.1.dist-info \
                /usr/include/python3.14/pygame

2) Make a venv and install pygame:

    cd ~
    python -m venv venv
    source venv/bin/activate
    pip install pygame-ce

3) Put paint11.py in your home folder. If you don't know where it
   downloaded to, find it:

    find ~ -name "paint11.py" 2>/dev/null

   Then copy whatever path that prints into home, e.g. if it's in Downloads:

    cp ~/Downloads/paint11.py ~/paint11.py

4) Run it:

    python ~/paint11.py


## Every time after that

A new terminal forgets the venv, so always do these two lines first:

    source ~/venv/bin/activate
    python ~/paint11.py

Open an image directly:

    python ~/paint11.py mypicture.png

Or just drag an image file onto the window.


## LAYERS  (the right-side panel like Windows 11 Paint)

- Press **Ctrl+L** to show / hide the Layers panel on the right.
- **+** button  : add a new (transparent) layer on top
- **⧉** button  : duplicate the selected layer
- **🗑** button  : delete the selected layer (can't delete the last one)
- **▲ / ▼**     : move the selected layer up / down in the stack
- Click a layer row to select it — you draw on the selected layer.
- Click the little **eye** on a row to hide / show that layer.
- The eraser now erases to transparent, so erasing on a top layer
  reveals whatever is on the layer beneath (just like W11 Paint).
- Save (Ctrl+S) flattens all visible layers into the image. Saving as
  .png keeps transparency.

Keyboard: Ctrl+L toggle panel · Ctrl+Shift+N new layer · Ctrl+Z undo.


## If you STILL get the font error on Python 3.14

Run it under Python 3.13 instead:

    sudo pacman -S python313
    python3.13 -m venv venv313
    source venv313/bin/activate
    pip install pygame-ce
    python ~/paint11.py
