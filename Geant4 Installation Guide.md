# Geant4 Installation Guide in WSL(Ubuntu)

Conrad Wang

## 1 Install dependent environment

### 1.1 C/C++ Compiler Environment

```bash
sudo apt install build-essential
```

### 1.2 qt5

```bash
sudo apt install qt5-defult qtcreator
#In order to adapt wsl ubuntu
sudo strip --remove-section=.note.ABI-tag /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
```

### 1.3 x11

```bash
sudo apt install x11-apps
```

### 1.4 OpenGL

```bash
sudo apt install libgl1-mesa-dev libglu1-mesa-dev libxt-dev libxmu-dev libxi-dev zlib1g-dev libgl2ps-dev libexpat1-dev libxerces-c-dev
```

## 2 Generate makefile

```bash
cmake -DCMAKE_INSTALL_PREFIX=/home/wangchunzheng/geant4/geant4.10.06.p02-install -DGEANT4_USE_OPENGL_X11=ON -DGEANT4_USE_RAYTRACER_X11=ON -DGEANT4_USE_GDML=ON -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_QT=ON ../geant4.10.06.p02
```

## 3 Make and install

```bash
make -j4
make install
```

## 4 Note

XLaunch do not check the option "Native opengl".

## Reference link

<http://geant4-userdoc.web.cern.ch/geant4-userdoc/UsersGuides/InstallationGuide/html/>