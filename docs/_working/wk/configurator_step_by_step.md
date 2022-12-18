# QMK Configurator: Step by Step

QMK Configurator를 통한 키보드 펌웨어 제작과정을 단계별로 설명합니다.

## Step 1: 키보드 선택

KEYBOARD 상자를 클릭해 키맵을 생성하려는 키보드를 선택하세요.

?> 사용하려는 키보드(기판)에 여러 버전이 존재하는 경우(예: dz60 rev1, rev2, ..) 올바른 버전이 선택되었는지 확인하세요.

진짜 중요한거니까 두 번 말합니다.

!> **올바른 버전을 선택했는지 확인하세요**

여러분의 키보드가 QMK로 작동한다고 명시되었으나 목록에 없는 경우, 이에 대한 활성화된 [Pull Request](https://github.com/qmk/qmk_firmware/pulls?q=is%3Aopen+is%3Apr+label%3Akeyboard)가 없다면 [qmk_firmware](https://github.com/qmk/qmk_firmware/issues) 로 알려주세요. 또한 제조업체의 GitHub 계정에 해당 키보드에 대한 정보가 존재할 수 있으니 참고하세요.

## Step 2: 키보드 레이아웃 선택

작성하려는 키맵에 적절한 레이아웃을 선택하세요. 일부 키보드는 충분한 레이아웃들이 준비되지 않았을 수 있으며, 이는 추후 지원될 예정입니다.

!> 원하는 것과 완벽히 맞는 레이아웃이 없는 경우, `LAYOUT_all`를 선택하세요.

## Step 3: 키맵 이름 정하기

여러분만의 키맵에 이름을 지어주세요.

?> 컴파일시 문제가 발생한다면, QMK Firmware repo에 이미 존재하는 이름을 사용했을 수 있으며 이 경우 다른 이름을 사용해 주세요.


## Step 4: 키맵 작성

키코드 입력은 다음 세 가지 방법으로 수행됩니다.

1. 드래그&드롭
2. 레이아웃의 빈 키 클릭 후, 원하는 키코드 클릭
3. 레이아웃의 빈 키 클릭 후, 키보드에서 원하는 키 입력

?> 키 위에 커서를 올리면 해당 키코드가 어떤 역할을 하는지 알려줍니다. 자세한 정보는 다음을 참고하세요:


* [Basic Keycode Reference](keycodes_basic.md)
* [Advanced Keycode Reference](feature_advanced_keycodes.md)

!> 선택한 레이아웃이 실제 물리적인 키보드 배열과 일치하지 않는 경우, 사용하지 않는 키는 빈칸으로 남겨두세요. BACKSPACE키가 하나인 키보드를 쓰는데 `LAYOUT_all`상에는 2개가 존재하는 등, 어떤 키가 실제 사용되는지 알 수 없다면 같은 키코드를 입력해주세요.



## Step 5: 향후 수정 위해 키맵 저장

키맵 작성을 끝냈거나 추후 이어서 작업하려면, `Download this QMK Keymap JSON File`버튼을 눌러 키맵을 컴퓨터에 저장합니다. `Upload a QMK Keymap JSON File`버튼으로 이 .JSON파일을 업로드해 이어서 작업할 수 있습니다.


!> **주의:** kbfirmware.com 등 다른 온라인 도구들과는 .json 양식이 달라 호환되지 않습니다.

## Step 6: 펌웨어 컴파일

`Compile` 버튼을 누르세요.

컴파일이 완료되면 `Download Firmware` 버튼으로 다운로드 합니다.

## Next steps: 키보드 플래싱

[Flashing Firmware](newbs_flashing.md) 문서로
