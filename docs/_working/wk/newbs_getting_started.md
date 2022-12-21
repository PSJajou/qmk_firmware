# QMK 환경설정

키맵 제작을 위해서는 먼저 몇몇 소프트웨어를 설치하고 개발환경을 갖춰야 합니다. 이 작업은 키보드 수와 관계 없이 한 번만 시행하면 됩니다.

## 1. 전제조건

개발에 앞서 필요한 소프트웨어는 다음과 같습니다.

* [텍스트 편집기](newbs_learn_more_resources.md#text-editor-resources)
  * 일반 텍스트 파일을 편집`저장할 수 있는 프로그램이 필요합니다. 대부분의 운영체제에 포함된 기본 편집기는 이를 지원하지 않으므로 확인해주세요.
* [Toolbox (optional)](https://github.com/qmk/qmk_toolbox)
  * 키보드 프로그래밍 및 디버깅을 지원하는 win/mac os용 그래픽 프로그램 입니다.

?> Linux/Unix의 command line 환경에서 작업해본 적이 없다면, 몇가지 기본적인 개념과 명령어는 알고있어야 합니다.
QMK 작업을 위해서는 [이 문서](newbs_learn_more_resources.md#command-line-resources) 를 읽어보는 정도로 충분할 것입니디ㅏ.

## 2. 개발환경 준비 :id=set-up-your-environment

Linux/Unix 환경만 준비해 놓으면, 나머지는 QMK가 설치하도록 두시면 됩니다.

<!-- tabs:start -->

### ** Windows **

QMK maintains a Bundle of MSYS2, the CLI and all necessary dependencies. It also provides a handy `QMK MSYS` terminal shortcut to boot you directly into the correct environment.

#### Prerequisites

You will need to install [QMK MSYS](https://msys.qmk.fm/). The latest release is available [here](https://github.com/qmk/qmk_distro_msys/releases/latest).

<details>
  <summary>Advanced Users</summary>

!> <b style="font-size:150%">This process is not recommended for new users.</b>

If you'd like to manually install MSYS2, the following sections will walk you through the process.

#### Prerequisites

You will need to install [MSYS2](https://www.msys2.org). Once installed, close any open MSYS terminals (purple icon) and open a new MinGW 64-bit terminal (blue icon) from the Start Menu.

!> **NOTE:** The MinGW 64-bit terminal is *not* the same as the MSYS terminal that opens when installation is completed. Your prompt should say "MINGW64" in purple text, rather than "MSYS". See [this page](https://www.msys2.org/wiki/MSYS2-introduction/#subsystems) for more information on the differences.

#### Installation

Install the QMK CLI by running:

    pacman --needed --noconfirm --disable-download-timeout -S git mingw-w64-x86_64-python-qmk

</details>

### ** macOS **

QMK maintains a Homebrew tap and formula which will automatically install the CLI and all necessary dependencies.

#### Prerequisites

You will need to install Homebrew. Follow the instructions on https://brew.sh.

#### Installation

Install the QMK CLI by running:

    brew install qmk/qmk/qmk

### ** Linux/WSL **

?> **Note for WSL users**: By default, the installation process will clone the QMK repository into your WSL home directory, but if you have cloned manually, ensure that it is located inside the WSL instance instead of the Windows filesystem (ie. not in `/mnt`), as accessing it is currently [extremely slow](https://github.com/microsoft/WSL/issues/4197).

#### Prerequisites

You will need to install Git and Python. It's very likely that you already have both, but if not, one of the following commands should install them:

* Debian / Ubuntu / Devuan: `sudo apt install -y git python3-pip`
* Fedora / Red Hat / CentOS: `sudo yum -y install git python3-pip`
* Arch / Manjaro: `sudo pacman --needed --noconfirm -S git python-pip libffi`
* Void: `sudo xbps-install -y git python3-pip`
* Solus: `sudo eopkg -y install git python3`
* Sabayon: `sudo equo install dev-vcs/git dev-python/pip`
* Gentoo: `sudo emerge dev-vcs/git dev-python/pip`

#### Installation

Install the QMK CLI by running:

    python3 -m pip install --user qmk

#### Community Packages

These packages are maintained by community members, so may not be up to date or completely functional. If you encounter problems, please report them to their respective maintainers.

On Arch-based distros you can install the CLI from the official repositories (NOTE: at the time of writing this package marks some dependencies as optional that should not be):

    sudo pacman -S qmk

You can also try the `qmk-git` package from AUR:

    yay -S qmk-git

###  ** FreeBSD **

#### Installation

Install the FreeBSD package for QMK CLI by running:

    pkg install -g "py*-qmk"

NOTE: remember to follow the instructions printed at the end of installation (use `pkg info -Dg "py*-qmk"` to show them again).

<!-- tabs:end -->

## 3. Run QMK Setup :id=set-up-qmk

<!-- tabs:start -->

### ** Windows **

After installing QMK you can set it up with this command:

    qmk setup

In most situations you will want to answer `y` to all of the prompts.

### ** macOS **

After installing QMK you can set it up with this command:

    qmk setup

In most situations you will want to answer `y` to all of the prompts.

### ** Linux/WSL **

After installing QMK you can set it up with this command:

    qmk setup

In most situations you will want to answer `y` to all of the prompts.

?>**Note on Debian, Ubuntu and their derivatives**:
It's possible, that you will get an error saying something like: `bash: qmk: command not found`.
This is due to a [bug](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=839155) Debian introduced with their Bash 4.4 release, which removed `$HOME/.local/bin` from the PATH. This bug was later fixed on Debian and Ubuntu.
Sadly, Ubuntu reintroduced this bug and is [yet to fix it](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/1588562).
Luckily, the fix is easy. Run this as your user: `echo 'PATH="$HOME/.local/bin:$PATH"' >> $HOME/.bashrc && source $HOME/.bashrc`

###  ** FreeBSD **

After installing QMK you can set it up with this command:

    qmk setup

In most situations you will want to answer `y` to all of the prompts.

<!-- tabs:end -->

?> The qmk home folder can be specified at setup with `qmk setup -H <path>`, and modified afterwards using the [cli configuration](cli_configuration.md?id=single-key-example) and the variable `user.qmk_home`. For all available options run `qmk setup --help`.

?> If you already know how to use GitHub, [we recommend that you follow these instructions](getting_started_github.md) and use `qmk setup <github_username>/qmk_firmware` to clone your personal fork. If you don't know what that means you can safely ignore this message.

## 4. Test Your Build Environment

Now that your QMK build environment is set up, you can build a firmware for your keyboard. Start by trying to build the keyboard's default keymap. You should be able to do that with a command in this format:

    qmk compile -kb <keyboard> -km default

For example, to build a firmware for a Clueboard 66% you would use:

    qmk compile -kb clueboard/66/rev3 -km default

When it is done you should have a lot of output that ends similar to this:

```
Linking: .build/clueboard_66_rev3_default.elf                                                       [OK]
Creating load file for flashing: .build/clueboard_66_rev3_default.hex                               [OK]
Copying clueboard_66_rev3_default.hex to qmk_firmware folder                                        [OK]
Checking file size of clueboard_66_rev3_default.hex                                                 [OK]
 * The firmware size is fine - 26356/28672 (2316 bytes free)
```

# Creating Your Keymap

You are now ready to create your own personal keymap! Move on to [Building Your First Firmware](newbs_building_firmware.md) for that.
