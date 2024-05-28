#! /bin/bash

if [ -z "$1" ] || [[ ! "$1" =~ "." ]] || [ -z "$2" ]; then
    echo "请按格式输入两个参数：姓名 工号"
    echo "举例：shaoka.wang 1450"
    exit
fi

# 获取用户名和工号
tpt_name="$1"
tpt_number="$2"

# 安装必需的包
sudo apt update

sudo apt install \
    vim cmake python3 python3-pip \
    docker.io gcc g++ clang llvm git \
    openjdk-17-jdk net-tools openssh-server \
    nfs-common openvpn cifs-utils doxygen \
    unzip wget curl gfortran binutils device-tree-compiler \
    bc ninja-build doxygen graphviz qemu qemu-system qemu-user

sudo apt upgrade
sudo apt autoremove

line=$(grep -n '192.168.0.201' /etc/hosts | cut -d: -f1 | head -n 1)
if [[ -n "$line" ]] && [[ "$line" =~ ^[0-9]+$ ]]; then
    sudo cp /etc/hosts /tmp/hosts.tmp
    sudo sed -i "${line},\$d" /tmp/hosts.tmp
    sudo cat /tmp/hosts.tmp | sudo tee /etc/hosts >/dev/null
    sudo rm /tmp/hosts.tmp
fi

# 设置HOSTS
echo -e "\n\n# Hefei Server\n192.168.0.201 git.tpt.hf.com\n192.168.0.202 jenkins.tpt.hf.com\n" | sudo tee -a /etc/hosts

# 挂载NAS
if [ ! -d "/share" ]; then
    sudo mkdir -p /share
fi

cd /share

if [ ! -d "home" ]; then
    sudo mkdir home
fi

if [ ! -d "public" ]; then
    sudo mkdir public
fi

if [ ! -d "web" ]; then
    sudo mkdir web
fi

echo -e "username=$tpt_name\npassword=tpt-$tpt_number\ndomain=WORKGROUP\n" | sudo tee /share/auth.smb >/dev/null
sudo chmod 600 /share/auth.smb

line=$(grep -n '192.168.0.28' /etc/fstab | cut -d: -f1 | head -n 1)
echo $line
if [[ -n "$line" ]] && [[ "$line" =~ ^[0-9]+$ ]]; then
    sudo cp /etc/fstab /tmp/fstab.tmp
    sudo sed -i "${line},\$d" /tmp/fstab.tmp
    sudo cat /tmp/fstab.tmp | sudo tee /etc/fstab >/dev/null
    sudo rm /tmp/fstab.tmp
fi

echo -e "\n\n//192.168.0.28/Home /share/home cifs _netdev,credentials=/share/auth.smb,uid=1000,gid=1000,nounix,sec=ntlmssp,iocharset=utf8 0 0\n//192.168.0.28/Public /share/public cifs _netdev,credentials=/share/auth.smb,uid=1000,gid=1000,nounix,sec=ntlmssp,iocharset=utf8 0 0\n//192.168.0.28/Web /share/web cifs _netdev,credentials=/share/auth.smb,uid=1000,gid=1000,nounix,sec=ntlmssp,iocharset=utf8 0 0\n" | sudo tee -a /etc/fstab
sudo mount -a

sudo rm /home
sudo ln -s /share /home

if [ -d "$HOME/Desktop" ]; then
    sudo rm "$HOME/Desktop"
    sudo ln -s /share "$HOME/Desktop"
elif [ -d "$HOME/桌面" ]; then
    sudo rm "$HOME/桌面"
    sudo ln -s /share "$HOME/桌面"
else
    true
fi

# 配置GIT
git config --global user.name "$tpt_name"
git config --global user.email "$tpt_name@terapines.com"

# 安装常用软件包
sudo apt install /share/public/archive/1110-ljh/enset/feishu.deb
sudo apt install /share/public/archive/1110-ljh/enset/edge.deb
sudo apt install /share/public/archive/1110-ljh/enset/vscode.deb
sudo apt install /share/public/archive/1110-ljh/enset/wps.deb


cd /opt
sudo rm -rf zstudio
sudo rm -rf gnu-sdk
sudo rm -rf riscv-toolchain
sudo rm -rf zcc-toolchain
sudo rm -rf andes-toolchain

sudo unzip /share/public/archive/1110-ljh/enset/zstudio.zip
sudo unzip /share/public/archive/1110-ljh/enset/gnu-sdk.zip
sudo unzip /share/public/archive/1110-ljh/enset/riscv-toolchain.zip
sudo unzip /share/public/archive/1110-ljh/enset/zcc-toolchain.zip
sudo unzip /share/public/archive/1110-ljh/enset/andes-toolchain.zip

sudo chmod -R 777 zstudio
sudo chmod -R 777 gnu-sdk
sudo chmod -R 777 riscv-toolchain
sudo chmod -R 777 zcc-toolchain
sudo chmod -R 777 andes-toolchain

echo -e '\n\nexport PATH=/opt/zcc-toolchain/bin:/opt/riscv-toolchain/elf/bin:/opt/riscv-toolchain/linux/bin:/opt/gnu-sdk/bin:$PATH:\n' >>$HOME/.bashrc

source ~/.bashrc


declare -a extensions=(
    "sunshaoce.RISC-V"
    "tboox.xmake-vscode"
    "ms-vscode.cpptools"
    "MS-CEINTL.vscode-language-pack-zh-hans"
    "twxs.cmake"
    "ms-vscode.cmake-tools"
    "formulahendry.code-runner"
    "cschlosser.doxdocgen"
    "yzhang.markdown-all-in-one"
    "ms-python.python"
    "terapines.tptest"
)

for extension in "${extensions[@]}"; do
        code --install-extension $extension --force
done

sudo apt update
sudo apt upgrade
sudo apt autoremove
