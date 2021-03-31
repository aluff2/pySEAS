# pySEAS

python Signal Extraction and Segmentation

---

# Installation Notes

should work with most python3s.  Currently being tested and developed on 3.8.

if some ffmpeg bindings aren't set correctly, mp4 videos may be difficult to load.  if so, use avis instead.

## Venvs

May help to create venv with system site packages for things like tk:
    
    python3.[X] -m venv <nameofyourenv> 

Manually install all dependencies with:

    pip install -r requirements.txt

Note the system site packages flag.  This allows the venv installation to access your systemwide tk installation.


## Tkinter

GUIs should work by default with base python installation, but you may need to install tk dependencies.

I've experienced issues getting tkinter to work on a python installation that isn't the most up to date version.  i.e. if you have 3.7 and 3.8 installed, tkinter on 3.7 might not work--try using 3.8.

Debian-based linux:

    sudo apt-get install python3.8 python3-tk python3.8-tk

If you experience problems with the GUI, check your tk version with the following terminal command:
    python -m tkinter
This will launch a GUI that tells you your tk version.  Make sure it is >=8.6

# Examples:

    python ica_project.py -f /home/sydney/Lab/testfiles/ -e 200220_01 -d 10 -r 1 -rr 2
    python ica_project.py -f /home/sydney/Lab/testfiles/ -e 170721_02 -d 10 -r 3


# TODO:

---

* clean up ROIs and other things in exp

* sharing test data?

* documentation

* clean up and unify script parameters

* better error than KeyError when experiment string was invalid.

* explicitly return ica_project output to bash.

# Developer Notes:

Using sphinx docstring documentation.

To load html docs locally:

from docs, run:

    make html

before committing, be sure to:

    make clean


To gather all modules and functions from the package, run from the project root:

    sphinx-apidoc -o docs seas

this only has to be done once.  For some reason it won't rerun once ./docs/seas.rst and ./docs/modules.rst are created, and keeps looking for files even if they were deleted.  Maybe there is a way to fix it, but I just deleted the extra module from modules.rst manually.

Settings are all in docs/conf.py, including modifying the system path to see the seas module. 

https://dev.to/dev0928/how-to-generate-professional-documentation-with-sphinx-4n78
https://www.sphinx-doc.org/en/master/usage/quickstart.html
https://stackoverflow.com/questions/2701998/sphinx-autodoc-is-not-automatic-enough