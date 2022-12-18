# 키보드 펌웨어 플래싱

커스텀 펌웨어 파일을 만들었으니, 이제 여러분의 키보드에 펌웨어를 집어넣을 차례입니다.

## 키보드 기판의 DFU (Bootloader) 모드 진입

커스텀 펌웨어를 덮어씌우기 위해서는, 우선 장치를 펌웨어 업데이트를 위한 DFU(Device Firmware Update)모드로 전환해야 합니다. 이 모드에서는 키보드 장치를 사용할 수 없으며, 펌웨어 업데이트 도중에 케이블이 뽑히는 등 어떤 사유로든 작업이 중단되어서는 안됩니다.

DFU모드 진입 방법은 제품마다 차이가 있습니다. 만약 이미 QMK, TMK 혹은 PS2AVRGB(Bootmapper client)로 작동중인 기판이면서 별도의 지침이 없다면, 다음의 방법들을 시도해보세요.

* 양쪽 shift 키를 누른 채로 `Pause`를 누르세요.
* 양쪽 shift 키를 누른 채로 `B`를 누르세요.
* 잠시 키보드 케이블을 뽑은 뒤, Spacebar와 `B`를 동시에 누른 채로 케이블을 연결하고 잠시 기다려보세요.
* 케이블을 뽑은 뒤, 키보드의 맨 왼쪽, 맨 위/아래 중 하나의 키(일반적으로 ESC 아니면 좌측 Ctrl)를 누른 채 케이블을 연결해보세요.
* 기판에 달린 `RESET` 버튼을 누르세요. 보통 기판 뒷면에 있습니다.
* 기판에서 `RESET` 과 `GND` 단자를 찾아 접지시켜보세요.

위 방법들이 모두 통하지 않고, 기판의 메인 칩에 `STM32`라 표기되어 있다면, 일반적으로 [Discord](https://discord.gg/Uq7gcHh)에 도움을 요청하는 것이 최선일 것입니다. 기판 사진 몇장을 준비해주시면 더 좋습니다.

DFU 진입에 성공하면 QMK Toolbox에 다음과 같은 노란색 메시지가 표시됩니다.

```
*** DFU device connected: Atmel Corp. ATmega32U4 (03EB:2FF4:0000)
```

해당 장치가 Device Manager, System Information.app, 혹은 `lsusb` 에도 표시됩니다.

## QMK Toolbox를 이용한 키보드 펌웨어 플래싱

키보드에 펌웨어를 플래싱 하는 가장 쉬운 방법은 [QMK Toolbox](https://github.com/qmk/qmk_toolbox/releases)를 사용하는 것입니다.

다만 QMK Toolbox는 Windows, Mac OS만 지원하므로, 여러분이 리눅스 OS를 사용한다면 [Flash your Keyboard from the Command Line](#flash-your-keyboard-from-the-command-line) 로 넘어가시면 됩니다.

### QMK Toolbox로 파일 로드하기

QMK Toolbox 프로그램을 열고 탐색기에서 펌웨어 파일을 찾습니다. 키보드 펌웨어는 `.hex` 혹은 `.bin` 파일 형식으로 저장되어 있습니다. QMK에서 장치에 적절한 파일을 `qmk_firmware` 디렉토리로 이동시킵니다.

Windows나 Mac OS의 경우, 다음 명령어를 이용해 빠르게 현재 폴더를 탐색기에 열 수 있습니다.

<!-- tabs:start -->

#### ** Windows **

```
start .
```

#### ** macOS **

```
open .
```

<!-- tabs:end -->

펌웨어 파일의 이름은 언제나 다음 형식을 따릅니다:

```
<keyboard_name>_<keymap_name>.{bin,hex}
```

예를 들어, `default` 키맵을 쓰는 `planck/rev5` 키보드의 펌웨어는 다음과 같은 이름으로 저장됩니다.

```
planck_rev5_default.hex
```

파일을 찾았다면 "Local file" 박스로 드래그하거나 "Open" 버튼을 눌러 파일을 선택합니다.

### 펌웨어 플래시

QMK Toolbox의 `Flash` 버튼을 누릅니다. 다음과 유사한 형태의 메시지와 함께 플래싱이 시작됩니다.

```
*** DFU device connected: Atmel Corp. ATmega32U4 (03EB:2FF4:0000)
*** Attempting to flash, please don't remove device
>>> dfu-programmer.exe atmega32u4 erase --force
    Erasing flash...  Success
    Checking memory from 0x0 to 0x6FFF...  Empty.
>>> dfu-programmer.exe atmega32u4 flash "D:\Git\qmk_firmware\gh60_satan_default.hex"
    Checking memory from 0x0 to 0x3F7F...  Empty.
    0%                            100%  Programming 0x3F80 bytes...
    [>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>]  Success
    0%                            100%  Reading 0x7000 bytes...
    [>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>]  Success
    Validating...  Success
    0x3F80 bytes written into 0x7000 bytes memory (56.70%).
>>> dfu-programmer.exe atmega32u4 reset
    
*** DFU device disconnected: Atmel Corp: ATmega32U4 (03EB:2FF4:0000)
```

## Flash your Keyboard from the Command Line

컴파일&펌웨어 업데이트 준비가 완료되면, 터미널 창에 다음 명령어를 실행합니다.

    qmk flash

CLI에서 [Configure your build environment](newbs_getting_started.md)에 따라 키보드/키맵 이름을 지정하지 않았거나, 여러 키보드를 사용중인 경우, 다음 명령어를 통해 키보드, 키맵을 선택합니다.

    qmk flash -kb <my_keyboard> -km <my_keymap>

이 명령은 키보드의 구성 정보를 확인하고, 지정된 부트로더에 따라 키보드를 플래시 합니다. 즉 당신이 부트로더 정보를 굳이 몰라도 상관 없으며, 귀찮은 일은 명령어가 알아서 해줄것입니다.

다만 키보드에 부트로더 정보가 지정되어 있지 않거나 지원되지 않는 다면, 다음과 같이 오류가 발생합니다.

    WARNING: This board's bootloader is not specified or is not supported by the ":flash" target at this time.

이 경우 부트로더를 직접 지정해 줘야 하며, 자세한 내용은 [Flashing Firmware](flashing.md) 를 참조해주세요.

!> `qmk flash`에서 부트로더가 감지되지 않는다면, `qmk doctor` 명령어를 실행해 해결책을 찾아볼 수 있습니다.

## 시험해보세요!

축하합니다! 여기까지 따라오셨다면, 여러분의 키보드를 위한 펌웨어는 이제 완성되어 테스트를 기다리고 있을 것입니다.

키보드 테스트는 그저 모든 키를 하나씩 눌러보며 올바른 값이 입력되는지 확인해보면 됩니다. [QMK Configurator](https://config.qmk.fm/#/test/)의 test 모드를 사용해 간단하게 입력테스트를 할 수도 있습니다.


뭔가 제대로 작동하지 않는 구석이 있다면 FAQ 항목 및[Discord 대화방](https://discord.gg/Uq7gcHh)을 참조해주세요.
