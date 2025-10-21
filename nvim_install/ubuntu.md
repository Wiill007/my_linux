## Prerequisites
```sh
sudo apt-get install ninja-build gettext cmake curl build-essential git
```

## Local installation from source
```sh
mkdir ~/libs
cd ~/libs
git clone https://github.com/neovim/neovim
cd neovim
git checkout stable
make CMAKE_BUILD_TYPE=RelWithDebInfo
sudo make install
```

## Add NvChad
```sh
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```