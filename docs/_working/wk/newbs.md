# The QMK Tutorial

우리가 쓰는 키보드에는 컴퓨터의 cpu와 유사한 프로세서가 들어있으며, 키보드의 스위치가 눌리는 것을 감지해 컴퓨터에 알리는 특별한 소프트웨어를 구동합니다. QMK는 바로 그 소프트웨어를 작성하는 도구입니다. 자신만의 키맵을 만드는 것은, 내 키보드를 위한 실행 프로그램을 만드는 것과 같습니다.

QMK는 쉬운일은 쉽게, 어려운 일은 어떻게든 가능하게 만들어 여러분의 손에 힘을 싣고자 합니다. 강력한 키맵을 만드는 데에 대단한 프로그래밍 스킬은 필요하지 않으며, 그저 간단한 구문 규칙만 따르면 됩니다.

Not sure if your keyboard can run QMK? If it's a mechanical keyboard you built yourself chances are good it can. We support a [large number of hobbyist boards](https://qmk.fm/keyboards/). If your current keyboard can't run QMK there are a lot of choices out there for boards that do.

여러분의 키보드가 QMK와 호환되는지 확신할 수 없나요? 직접 제작한 기계식 키보드 라면 아마도 될 것입니다. [호환되는 키보드 목록](https://qmk.fm/keyboards/)


?> **나는 코딩이 싫어요**<br>
프로그래밍에 대해 생각만 해도 머리가 아파온다면 대신 [온라인 GUI 도구](newbs_building_firmware_configurator.md)를 사용하는 것도 고려해보세요.</div>

## Overview

이 가이드는 소스코드를 통해 키보드 펌웨어를 만들고자 하는 분들을 위한 내용을 담고 있습니다. 아마 프로그래밍이 익숙한 분들은 각 과정이 굉장히 따라하기 쉽다는 것을 알 수 있을 것입니다. 가이드는 다음과 같이 3개의 주요 섹션으로 나뉩니다:

1. [개발환경 설정](newbs_getting_started.md)
2. [첫 펌웨어 제작](newbs_building_firmware.md)
3. [펌웨어 플래싱](newbs_flashing.md)

본 가이드는 소프트웨어 제작 경험이 없는 이들이 읽을 것을 전제로 전개됩니다. 따라서 많은 작업들은 여러 대안이 존재하며, 저희는 그것들을 존중합니다. 각 작업의 수행에 대해 궁금한 점이 있다면 [저희에게 안내를 요청할 수 있습니다](getting_started_getting_help.md).

## Additional Resources

이 가이드 외에도 QMK를 배우는 데에 도움이 될만한 내용들이 있습니다.
 * [Syllabus](syllabus.md)
 * [Learning Resources](newbs_learn_more_resources.md)