# QMK 환경설정

키맵 제작을 위해서는 먼저 몇몇 소프트웨어를 설치하고 개발환경을 갖춰야 합니다. 이 작업은 키보드 수와 관계 없이 한 번만 시행하면 됩니다.

## 1. 필수 요구사항

개발에 앞서 필요한 소프트웨어는 다음과 같습니다.

* [텍스트 편집기](newbs_learn_more_resources.md#text-editor-resources)
  * 일반 텍스트 파일을 편집`저장할 수 있는 프로그램이 필요합니다. 대부분의 운영체제에 포함된 기본 편집기는 이를 지원하지 않으므로 확인해주세요.
* [Toolbox (optional)](https://github.com/qmk/qmk_toolbox)
  * 키보드 프로그래밍 및 디버깅을 지원하는 win/mac os용 그래픽 프로그램 입니다.

?> Linux/Unix의 command line 환경에서 작업해본 적이 없다면, 몇가지 기본적인 개념과 명령어는 알고있어야 합니다.
QMK 작업을 위해서는 [이 문서](newbs_learn_more_resources.md#command-line-resources) 를 읽어보는 정도로 충분할 것입니디ㅏ.

## 2. 개발환경 구성 :id=set-up-your-environment

Linux/Unix 환경의 경우, QMK가 알아서 설치하도록 두면 됩니다.

<!-- tabs:start -->

### ** Windows **

QMK는 MSYS2 번들, CLI 및 모든 의존요소들을 유지보수하며,  올바른 환경에서 바로 부팅하기 편하도록 `QMK MSYS` 터미널 바로가기를 제공합니다.

#### 준비물

[QMK MSYS](https://msys.qmk.fm/)를 설치해야 합니다. [이곳에서](https://github.com/qmk/qmk_distro_msys/releases/latest) 최신 버전을 받을 수 있습니다.

<details>
  <summary>Advanced Users</summary>

!> <b style="font-size:150%">이 작업은 초보자에게 권장하지 않습니다.</b>

MSYS2를 수동으로 설치하고자 한다면 다음 안내를 따라주세요.

#### 준비물

우선 [MSYS2](https://www.msys2.org)를 설치한 후, 열려있는 MSYS 터미널(보라색 아이콘)들을 모두 닫습니다. 그후 새 MinGW 64-bit 터미널을 시작메뉴에서 실행합니다.

!> **NOTE:** MinGW 64-bit 터미널과 설치시 열리는 MSYS 터미널은 *다릅니다*. 프롬프트에 "MSYS"가 아닌 "MINGW64"가 보라색으로 표시되야 하며, 그외 상세한 차이점은 [이 페이지를](https://www.msys2.org/wiki/MSYS2-introduction/#subsystems) 참고해주세요.


#### 설치

다음 명령어로 QMK CLI를 설치합니다:

    pacman --needed --noconfirm --disable-download-timeout -S git mingw-w64-x86_64-python-qmk

</details>

### ** macOS **

QMK는 CLI와 모든 필요한 의존요소를 자동으로 설치하는 Homebrew tap과 formula를 유지보수하고 있습니다.

#### 준비물

Homebrew를 설치해야 합니다. https://brew.sh. 를 따라주세요.

#### 설치

다음 명령어로 QMK CLI를 설치합니다:

    brew install qmk/qmk/qmk

### ** Linux/WSL **

?> **Note for WSL users**: 기본적으로 설치작업시 QMK repository를 WSL의 home directory로 복사하지만, 만약 수동으로 복사했다면 Windows filesystem이 아닌 WSL 인스턴스에 제대로 위치했는지 확인해주세요. 접근 속도가 [매우 느려질 수 있습니다.](https://github.com/microsoft/WSL/issues/4197)

#### 준비물

Git과 Python을 설치해야 합니다. 둘중 설치되지 않은 것이 있다면 다음 명령어들을 이용해 설치해주세요:

* Debian / Ubuntu / Devuan: `sudo apt install -y git python3-pip`
* Fedora / Red Hat / CentOS: `sudo yum -y install git python3-pip`
* Arch / Manjaro: `sudo pacman --needed --noconfirm -S git python-pip libffi`
* Void: `sudo xbps-install -y git python3-pip`
* Solus: `sudo eopkg -y install git python3`
* Sabayon: `sudo equo install dev-vcs/git dev-python/pip`
* Gentoo: `sudo emerge dev-vcs/git dev-python/pip`

#### 설치

다음 명령어로 QMK CLI를 설치합니다:

    python3 -m pip install --user qmk

#### Community Packages

이 패키지들은 커뮤니티 구성원들에 의해 유지 관리되므로, 최신상태가 아니거나 제대로 작동하지 않을 수 있습니다. 문제 발생시 해당 관리자에게 알려주세요.

On Arch-based distros you can install the CLI from the official repositories (NOTE: at the time of writing this package marks some dependencies as optional that should not be):

    sudo pacman -S qmk

You can also try the `qmk-git` package from AUR:

    yay -S qmk-git

###  ** FreeBSD **

#### 설치

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
