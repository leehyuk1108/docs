<!-- Korean default README for the korean branch. Original English source: README.en.md and https://github.com/ophwug/docs -->

> [!NOTE]
> 이 브랜치에서는 한국어 번역본을 기본 README로 표시합니다. 영어 원문은 [README.en.md](README.en.md)에 보관되어 있습니다. 원문의 구조, 링크, 사례 구분을 최대한 유지하면서 자연스러운 한국어로 옮겼습니다. 기술 용어와 제품명은 원문과 대조하기 쉽도록 대체로 그대로 두었습니다.

[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/leehyuk1108/docs)

<a id="unofficial-documentation-of-unofficial-fixes-and-tweaks-to-comma-and-unofficial-openpilot-hardware"></a>
# comma 및 비공식 openpilot 하드웨어의 비공식 수리/조정 문서

[comma.ai Discord][cdiscord]는 하드웨어 수리와 유지보수에 관한 질문의 _답변_ 이나 안내를 보관하기에 그다지 좋은 장소가 아닙니다.
Discord 검색은 매우 좋지 않고, 안에 있는 내용은 검색 엔진에서도 접근할 수 없습니다.
이 문서는 Discord에서 논의된 흔한 문제와 해결책을 공개 인터넷에 정리해서, 검색 엔진으로 찾을 수 있게 하려는 시도입니다.

> [!TIP]
> 이 문서는 매우 깁니다. 출력하면 **50페이지 이상**입니다. 한 번에 전부 집중해서 읽을 필요는 전혀 없습니다. **🤖 AI 어시스턴트를 사용해 관련 섹션을 더 빠르게 찾으세요.**
>
> 인용과 참고 문헌을 함께 보며 질문하기에는 [DeepWiki](https://deepwiki.com/leehyuk1108/docs)가 좋은 선택이라 추천합니다.
>
> * DeepWiki는 최신 문서보다 일주일 정도 늦을 수 있습니다.
> * DeepWiki가 이미지를 보거나 표시하지 못할 수 있으므로, 원문 섹션도 함께 확인하세요.
>
> DeepWiki를 사용하려면 아래 링크로 이동한 뒤 채팅 인터페이스에 질문을 입력하면 됩니다.
>
> https://deepwiki.com/leehyuk1108/docs
>
> [![deepwiki 데모 애니메이션](https://github.com/user-attachments/assets/f14e8dda-f7ca-457c-a358-3a2fc1a666ae)](https://deepwiki.com/leehyuk1108/docs)
>
> openpilot 하드웨어에 대해 [![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/leehyuk1108/docs)에 물어보세요!
>
> DeepWiki가 이 문서를 제대로 해석하고 있는지 확신이 없다면, Discord에 DeepWiki 대화 링크를 공유해도 좋습니다.
>
> 물론 [ChatGPT](https://chat.openai.com/chat), [Claude](https://claude.ai/), [Gemini](https://gemini.google.com) 같은 다른 🤖 AI 어시스턴트도 이 저장소 URL을 전달하면 사용할 수 있습니다: https://github.com/ophwug/docs

> [!WARNING]
> **항상 원 출처로 검증하세요**: DeepWiki나 어떤 AI 어시스턴트를 사용하든, 이 문서에서 인용한 원문과 이미지를 반드시 확인하세요. AI 어시스턴트는 이미지나 도표를 제대로 해석하지 못할 수 있고, 시각 자료에 대한 이해가 불완전하거나 부정확할 수 있습니다. openpilot 커뮤니티 안에서 잘못된 편향을 가질 수도 있습니다. 중요한 정보는 항상 원본 자료와 대조하세요. 이 경고는 DeepWiki만이 아니라 모든 AI 어시스턴트에 적용되며, 이 문서에만 한정되는 경고도 아닙니다.
>

[이 문서에는 comma.ai가 아닌 다른 Discord 링크도 포함될 수 있습니다.](#discords-and-discussions-of-note)

이 문서는 사례별로 구성되어 있습니다. 자신의 사례, pull request, 해결책을 자유롭게 추가해 주세요.

이 문서는 공식 문서가 아니며 comma.ai의 보증이나 승인을 받은 문서도 아닙니다. 다만 여러분 같은 사용자와 독자의 도움으로 유지되고 있으니, 제안이나 pull request를 편하게 보내 주세요.

또한 해결 방법이 실제로 효과가 있었는지, 없었는지도 꼭 알려 주세요. Discord, GitHub issue 등 어디든 좋습니다. **이 문서는 살아 있는 문서입니다!**

Amazon 링크는 Amazon Affiliate 링크일 수 있습니다. 해당 링크로 구매하면 구매자에게 추가 비용 없이 제게 작은 수수료가 지급될 수 있습니다. 이 수익은 이런 사례를 문서화하기 위한 소모품, 서비스, 도구 구매를 지원하는 데 쓰입니다.

<a id="table-of-contents"></a>
## 목차

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

  - [주목할 만한 Discord와 논의](#discords-and-discussions-of-note)
  - [일반 참고 사항](#general-notes)
  - [예방 및 권장 조치](#preventative-and-recommended-measures)
  - [하드웨어 문서](#hardware-documentation)
    - [공식 하드웨어 문서](#official-hardware-documentation)
    - [리버스 엔지니어링된 커뮤니티 클론 및 대체 하드웨어 문서](#reverse-engineered-community-clones-and-alternative-hardware-documentation)
    - [분류](#taxonomy)
      - [Panda](#panda)
      - [comma.ai Harness](#commaai-harness)
  - [모든 comma 기기에 공통](#common-to-all-comma-devices)
    - [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)
    - [OBD-C 케이블이 하네스 박스에 완전히 꽂히지 않은 사례](#the-not-fully-inserted-obd-c-cable-into-harness-box-case)
    - [OBD-C 포트 불량 사례](#the-bad-obd-c-port-case)
    - [차량 하네스 불량 사례](#the-bad-car-harness-case)
    - [IR 블래스터 불량 사례](#the-bad-ir-blaster-case)
    - [너무 오래된 OS를 실행 중인 사례](#the-running-too-old-of-an-os-case)
  - [모든 comma two 계열 기기에 공통](#common-to-all-comma-two-family-devices)
    - [comma two에서 Wi-Fi가 인터넷에 연결되지 않아 설치를 진행할 수 없는 사례](#the-cant-proceed-to-installation-because-wi-fi-cant-connect-to-internet-case-on-my-comma-two)
  - [모든 comma three 계열 기기에 공통](#common-to-all-comma-three-family-devices)
    - [부팅 시 빌드 오류 사례](#the-build-error-on-boot-case)
    - [OS가 꼬인 사례](#the-os-is-messed-up-case)
    - [퓨즈가 나간 사례](#the-blown-fuse-case)
    - [슈퍼커패시터 불량 사례](#the-bad-supercapacitor-case)
    - [화면이 작동하지 않거나 죽어 가는 사례](#the-screen-doesnt-work-or-is-dying-case)
    - [팬 사망 사례](#the-fan-death-case)
    - [청소되지 않은 팬 플럭스 사례](#the-uncleaned-fan-flux-case)
    - [GPS 신호 불량 사례](#the-poor-gps-signal-case)
    - [SOM 불량 또는 사망 사례](#the-bad-or-dead-som-case)
    - [리본 케이블 손상 사례](#the-damaged-ribbon-cable-case)
    - [SIM 카드가 끼인 사례](#the-sim-card-is-stuck-case)
    - [등록에서 멈춘 사례](#the-stuck-on-registration-case)
    - [화면 커넥터 EMI 필터 불량 사례](#the-bad-screen-connector-emi-filters-case)
  - [comma three (C3)](#comma-three-c3)
    - [축축했던 No Panda 사례](#the-swampy-no-panda-case)
    - [화면 색상이 매우 이상한 사례](#the-screen-colors-are-really-off-case)
    - [MOSFET이 탄 사례](#the-burned-mosfet-case)
    - [카메라 오작동 사례 (C3)](#the-camera-malfunction-case-c3)
    - [NVMe 드라이브가 마운트되지 않는 사례](#the-nvme-drive-not-mounted-case)
  - [comma threex (C3X)](#comma-threex-c3x)
    - [C3X의 No Panda 사례 (소프트웨어)](#the-no-panda-on-c3x-case-software)
    - [C3X의 No Panda 사례 (하드웨어)](#the-no-panda-on-c3x-case-hardware)
    - [C3X의 Panda가 타 버린 사례](#the-fried-panda-case-c3x)
    - [C3X의 와이드 카메라 오작동 사례](#the-wide-camera-malfunction-case-c3x)
    - [Step-down DC/DC 레귤레이터 불량 사례](#the-bad-step-down-dcdc-regulator-case)
    - [전원 IC (MP1701) 불량 사례](#the-bad-power-ic-mp1701-case)
  - [comma four (C4)](#comma-four-c4)
    - [케이블이 끝까지 꽂히지 않은 사례 (C4)](#the-cable-not-plugged-in-all-the-way-case-c4)
- [함께 보기](#see-also)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<a id="discords-and-discussions-of-note"></a>
## 주목할 만한 Discord와 논의

Discord 대화로 이어지는 링크가 포함될 수 있습니다.

채널 링크가 작동하려면 해당 초대 링크로 서버에 참여해야 합니다.

* [comma.ai Discord (표시가 없고 Discord 링크라면 보통 이 서버입니다)](https://discord.comma.ai/)
  * [#hw-three-3x](https://discord.com/channels/469524606043160576/871838269405556736)
* [openpilot enthusiasts Discord (OPC), 파생된 별도 커뮤니티 Discord](https://discord.gg/rRB7eDKccy)

이 문서는 대체로 [#hw-three-3x](https://discord.com/channels/469524606043160576/871838269405556736) 여기저기에서 논의됩니다. 다만 이 저장소의 [GitHub issues](https://github.com/ophwug/docs/issues)에 issue를 만들고 논의해도 됩니다.

<a id="general-notes"></a>
## 일반 참고 사항

> [!CAUTION]
> **OBD-C는 협상 없이 12V를 출력합니다. 5V가 아닙니다!** 하네스 박스는 OBD-C 포트로 즉시 12V를 출력하며, 이는 **정상적이거나 규격을 준수하는 USB-PD 포트가 아닙니다**. 전원 협상을 전혀 하지 않고, **연결 즉시 12V를 직접 공급합니다**. 물리적으로 USB-C 커넥터와 비슷하더라도, 하네스 박스의 OBD-C 포트에 일반 USB-C 기기(휴대폰, 태블릿, 노트북 등)를 **절대 연결하지 마세요**. 그렇게 하면 연결된 기기가 **손상되거나 파손됩니다**. OBD-C는 comma 기기와 이 포트에서 12V 입력을 받도록 특별히 설계된 기기에만 호환됩니다.

* **출발점으로, 문제가 소프트웨어와 관련된 것이 아닌지 확인하기 위해 반드시 stock openpilot 또는 comma openpilot을 먼저 설치하세요.**
  * stock 또는 comma openpilot을 실행하고 있지 않으면 comma.ai support는 도와주지 않습니다.
  * comma Discord는 `#custom-forks` 외부에서는 comma openpilot만 지원합니다.
  * 차량 지원 문제 등으로 stock 또는 comma openpilot을 설치할 수 없다면, `#custom-forks`에서 이야기하거나 사용하는 fork의 Discord에서 문제를 논의하세요.
* 기기가 반품 또는 보증 기간 안에 있다면 [먼저 comma.ai support에 문의해야 합니다.](https://comma.ai/support)
  * 새 comma 기기의 보증 기간은 패키지가 도착한 날부터 1년입니다. ([출처](https://comma.ai/shop/comma-3x))
  * [⏱️ “보증 기간에서 밀려날까 걱정하는 분들을 위해 말하자면, 반품/보증 기간 전에 티켓이 열렸다면 괜찮습니다.” - adeeb, comma staff lead](https://www.reddit.com/r/Comma_ai/comments/1nhs5ho/comment/nedq5kl/?context=3)
  * support 티켓을 제출할 때 “주행 중 발생한다”는 취지의 옵션을 선택하면, 티켓 진행을 위해 “route”를 제공하라는 질문이 나옵니다. op-replay-clipper 도구의 간단 사용 가이드(https://github.com/nelsonjchen/op-replay-clipper)를 5단계까지 따르면 URL이 생성됩니다. 업로드에 관한 4단계는 건너뛰어도 됩니다. 그 URL을 comma support가 요청하는 “route”로 제공할 수 있습니다. 안타깝게도 comma는 route가 무엇인지, 어떻게 얻는지 설명하는 오래된 문제를 아직 해결하지 않았기 때문에, 현재로서는 그 도구의 안내가 가장 나은 문서입니다.
    * comma connect에 아무것도 보이지 않거나 route를 생성할 수 없다면, “주행 중 발생한다”에 대한 부정 선택지를 고른 뒤 실제로는 주행 중 발생한다고 설명하세요.
* C3X가 보증 기간이 지났다면, comma에서 수리받는 대략적인 비용은 [C3X Out Of Warranty Repair 서비스 기준 $500](https://comma.ai/shop/comma-3x-out-of-warranty-repair)입니다.
  * 안타깝게도 이 수리에는 보증이 없습니다.
  * 다만 이 문서의 [퓨즈가 나간 사례](#the-blown-fuse-case)에서 rifkers를 검색해 보면, Chase Sapphire Preferred 카드로 연장 보증을 받을 수 있었던 것으로 보입니다. 경우에 따라 다를 수 있습니다.
* [comma는 더 이상 C3를 수리하지 않습니다. C3를 C3X로 $750에 교환하는 trade-in 프로그램만 제공합니다.](https://comma.ai/shop/comma-3x-trade-in)
* 이 문서의 많은 정보는 사용자 경험을 바탕으로 하며 정확하지 않을 수 있습니다.
* 모바일 수리점, 비디오 게임 하드웨어 수리점, PCB 전자 수리 업체 및 비슷한 곳들이 하드웨어 수리에 도움을 줄 수 있습니다. 결과는 다를 수 있고, 솔직히 이런 기기는 흔하지 않지만 구체적인 지침이 있으면 도움을 줄 의향이 있을 수도 있습니다.
* 문제가 지속되는지 평가하기 전에 기기의 전원을 뽑고 30분 동안 완전히 꺼 두세요.
* 수리를 맡길 계획이더라도 멀티미터는 가지고 있는 것이 좋습니다. 이 일뿐 아니라 다른 집수리나 생활 프로젝트에도 정말 유용합니다.
  * 비싼 것이 필요하지는 않습니다. Amazon이나 대형 매장에서 파는 간단한 ~$30짜리면 충분합니다. 예: https://amzn.to/3IBI4LF
* 문제가 차량 자체에 있는 것이 아닌지 확인하세요. 차량 커넥터를 모두 순정 상태로 분리했다가 다시 연결해 차량이 정상 작동하는지 확인하세요.
* 직접 분해한다면, 분해한 모든 부품을 추적하고 빠진 부품 없이 다시 조립할 수 있도록 깨끗하고 좋은 작업 공간을 마련하세요. 나사 매트나 작은 용기가 필요할 수 있습니다.
* 수리를 시도하기 전에 문제를 제대로 진단하는 것이 중요합니다. 잘못된 부품을 수리하려고 하면 추가 손상으로 이어질 수 있습니다.

<a id="preventative-and-recommended-measures"></a>
## 예방 및 권장 조치

아래 내용을 전부 할 필요는 없지만, 기기의 수명을 늘리거나 접근 권한을 보존하는 데 도움이 될 수 있습니다.

comma 기기는 무적이 아닙니다. 사람과 삶의 다른 모든 것처럼 [고장률의 욕조 곡선](https://en.wikipedia.org/wiki/Bathtub_curve)을 따릅니다.

![욕조 곡선 도표](https://upload.wikimedia.org/wikipedia/commons/thumb/7/78/Bathtub_curve.svg/960px-Bathtub_curve.svg.png)

충분히 긴 시간축에서는 모든 기기가 결국 고장납니다.

* 사용하지 않을 때나 고온 환경에서는 차량에서 기기를 제거할 수 있는 방법을 마련하세요.
  * 순정 comma 하드웨어는 영구 설치를 전제로 설계되어 자주 탈거하도록 만들어지지 않았습니다. 기기를 탈거하면 특히 OBD-C(USB와 비슷한) 케이블에 마모가 생길 수 있습니다.
  * 기기를 자주 제거하고 싶다면 자석식 또는 빠른 탈착식 마운트를 사용하세요.
    * 이런 마운트는 케이블과 커넥터의 무결성을 보존하는 데 도움이 됩니다.
    * [몇 가지 제안은 comma의 #hw-unofficial 채널을 참고하세요.](https://discord.com/channels/469524606043160576/534139378772082749)
    * #hw-unofficial 채널 아래에는 [자석식 마운트](https://discord.com/channels/469524606043160576/1130905705784803510)에 관한 전용 스레드도 있습니다.
    * 충격과 긁힘으로부터 기기를 보호하려면 실리콘 케이스를 사용하세요.
      * [Soft Silicone Case (Only for Openpilot Comma3X) – Janka's Workshop](https://janquick.com/products/soft-silicone-case-only-for-c3x)
* 기기를 제거할 때는 OBD-C 케이블을 조심하세요. 물리적으로 조심하는 것뿐 아니라, 끝부분을 포함한 케이블을 햇빛의 손상시키는 광선으로부터 숨기는 것도 수명을 늘리는 데 도움이 됩니다.
* 기기를 제거할 때는 OBD-C 포트도 조심하세요. 설계상 약한 지점이라 주의하지 않으면 손상될 수 있습니다. 이는 OBD-C 케이블보다 훨씬 고치기 어렵습니다. OBD-C 포트 마모를 줄이기 위해 자석식 마운트를 검토하세요.
* 정품 comma 기기에서는 SSH로 접속해 `/persist/comma/id_rsa` 내용을 백업하세요.
  * https://spektor56.github.io/OpenpilotToolkit/ 는 이를 쉽게 할 수 있는 도구입니다.
  * 더 수동적인 절차는 https://github.com/commaai/openpilot/wiki/SSH 에서 확인할 수 있지만 UI가 자주 바뀌는 듯합니다. 큰 흐름은 같습니다.
  * CPU, 메모리 및 기타 핵심 부품이 들어 있는 주 처리 장치인 System-On-Module(SOM)을 교체해야 하는 상황이 생기면, 이 파일을 사용해 comma 서버 접근 권한을 복원할 수 있습니다. 이 파일 없이는 서버 접근 권한을 다시 얻는 것이 불가능합니다. **이 파일은 comma 서버와 [comma connect](https://connect.comma.ai)에 대한 당신의 라이선스입니다. comma는 이 라이선스 파일을 잃어버려도 절대 다시 발급해 주지 않습니다.**
  * [최신 comma openpilot 버전은 self-driving 기능을 활성화하려면 이 파일이 존재해야 합니다.](https://github.com/commaai/openpilot/commit/f4b017a75b0ba59bb1540347b101293c3db7364d) 다만 fork는 이 파일을 요구하지 않도록 선택할 수 있습니다.
* 자석식 케이블 어댑터는 사용하지 마세요. OBD-C는 USB-C보다 핀이 잘못된 곳에 연결되는 것에 훨씬 민감하므로, OBD-C용으로 설계된 자석식 또는 quick release 마운트를 사용하세요.
* **하네스 박스의 OBD-C 포트에 일반 USB-C 기기를 절대 연결하지 마세요**. 하네스 박스는 5V가 아니라 12V를 출력하며, 5V를 기대하는 기기(휴대폰, 태블릿, 노트북 등)를 손상시키거나 파손합니다.

<a id="hardware-documentation"></a>
## 하드웨어 문서

<a id="official-hardware-documentation"></a>
### 공식 하드웨어 문서

comma.ai는 일부 하드웨어에 대한 공개 문서를 https://github.com/commaai/hardware/ 에 보관합니다.

완전한 목록은 아니지만, 포함된 항목은 다음과 같습니다.

* 하네스 pinout
* 마운트용 3D STL
  * 3X: https://github.com/commaai/hardware/tree/master/comma_3X/mount
* [Harness box v3 회로도](https://github.com/commaai/hardware/blob/master/harness/v3/Harness_Box.pdf)
  * Solid State Relay

<a id="reverse-engineered-community-clones-and-alternative-hardware-documentation"></a>
### 리버스 엔지니어링된 커뮤니티 클론 및 대체 하드웨어 문서

공식 문서는 아니지만 참고용으로 충분히 가까울 수 있습니다.

* https://github.com/lukasloetkolben/OpenpilotHardware
  * [Harness Box v1](https://github.com/lukasloetkolben/OpenpilotHardware/tree/main/HarnessBox)
    * 물리 릴레이
  * 그 외 더 있음!

<a id="taxonomy"></a>
### 분류

comma 기기, 클론, 하드웨어의 분류에 관한 작고 불완전한 로컬 문서입니다.

더 자세한 내용은 각각의 문서를 참고하세요.

<a id="panda"></a>
#### Panda

panda는 컴퓨터가 차량과 통신할 때 사용하는 CAN 인터페이스이고, 하네스는 차량 인터페이스입니다. 때로 사람들은 comma 하네스를 panda로 착각하지만, 둘은 다른 것입니다. comma two 및 그 이후 기기에서는 panda가 기기 자체에 통합되어 있습니다. 예외는 외장 [red panda](https://comma.ai/shop/panda)로, CAN-FD 차량에서 comma three와 함께 사용됩니다.

이 이름은 [원래 panda 동글 또는 어댑터가 흑백이었기 때문에](https://techcrunch.com/2017/07/07/comma-ai-launches-an-88-universal-car-interface-called-panda/) 붙었습니다.

* White Panda: CAN 전용이며 구형 comma 구성에서 OBD-II 또는 OBD-II와 비슷한 포트에 연결됨
  * EON 기기 구성에서는 외장형
  * [외장 어댑터로 판매된 적 있음](https://comma.ai/shop/panda)
  * 오래전에 지원이 중단됨
* Black Panda: CAN 전용
  * comma two 기기에 통합됨
  * comma three 기기에 통합됨
  * [차량 하네스에서 OBD-C를 입력받는 외장 어댑터로 판매된 적 있음](https://comma.ai/shop/panda)
  * C3 지원이 중단되었을 때(2025-08-26), comma는 [panda GitHub 저장소](https://github.com/commaai/panda)에서도 소프트웨어 지원을 중단하고 제거했습니다.
* Red Panda: CAN 및 CAN-FD 지원
  * comma threex 기기에 통합됨
  * comma four 기기에 통합됨
  * [차량 하네스에서 OBD-C를 입력받는 외장 어댑터로 판매됨](https://comma.ai/shop/panda)

<a id="commaai-harness"></a>
#### comma.ai Harness

> [!CAUTION]
> **하네스 박스는 OBD-C로 12V를 출력합니다. 5V가 아닙니다!** OBD-C 포트는 **정상적이거나 규격을 준수하는 USB-PD 포트가 아닙니다**. 전원 협상을 하지 않으며, **연결 즉시 12V를 직접 공급합니다**. USB-C 물리 커넥터를 사용하더라도, 일반 USB-C 기기(휴대폰, 태블릿, 노트북 등)를 하네스 박스의 OBD-C 포트에 **절대 꽂지 마세요**. 손상되거나 파손됩니다. comma 기기나 12V 입력을 받도록 특별히 설계된 기기만 연결하세요.

comma.ai 하네스는 릴레이 박스(하네스 박스라고도 부름)를 통해 차량과 comma 기기를 연결합니다. 릴레이 박스는 OBD-C 포트를 통해 전원과 데이터 신호를 출력합니다.

**릴레이 박스, 하네스 케이블, comma power가 포함된 Harness V3 (~2024년 6월부터 배송)**:

![이미지](https://github.com/user-attachments/assets/e7fc1e9f-071b-46f7-a5db-6964a0fb4522)

**물리 릴레이가 있는 박스(정상 동작 중 클릭 소리가 들림), 하네스 케이블, comma power가 포함된 Harness V1**:

![이미지](https://github.com/user-attachments/assets/83a7e287-c6bc-43ab-800d-5763098b1645)

![이미지](https://github.com/user-attachments/assets/6e630048-13fb-453d-9401-bf75709209c2)

![이미지](https://github.com/user-attachments/assets/eab842c7-edaf-4125-b9ab-b55c82579502)

그리고 flat CAT6 7ft 케이블이 추가됩니다. https://www.monoprice.com/product?p_id=43077

> [!CAUTION]
> **하네스 박스의 RJ45 포트는 Ethernet 포트가 아닙니다!** 이 포트를 라우터, 스위치, 컴퓨터 또는 다른 Ethernet 장비에 연결하면 연결된 장비가 **손상되거나 파손됩니다**. 이 포트는 차량 하네스용 12V 전원과 CAN bus 신호를 운반하며, 표준 네트워크 장비와 호환되지 않습니다. 네트워크 장비에서 나온 Ethernet 케이블을 이 포트에 **절대 꽂지 마세요**.

시각적으로나 물리적으로나 Harness V1과 V3는 매우 다릅니다. Harness V3 릴레이 박스는 3D 프린트가 아닌 성형 케이스를 사용하고, 릴레이 박스 자체가 훨씬 작으며, 릴레이/하네스 박스에 연결되는 하네스 커넥터 포트가 더 작고 얇습니다. 또한 comma power 부분은 OBD-2 포트에 연결할 때 CAT6나 Ethernet 케이블을 사용하지 않습니다. 전체적으로 V3가 더 작습니다. V3 릴레이 박스는 solid state 방식이라 물리 릴레이가 없으며, 이는 [차량 하네스 불량 사례](#the-bad-car-harness-case)에 더 잘 견디는 데 도움이 됩니다.

Harness V1 차량 하네스는 Harness V3와 호환되지 않으며, 반대도 마찬가지입니다. 다만 출력으로 사용하는 OBD-C 케이블과 포트는 같습니다.

comma two는 Harness V1과만 호환됩니다. Harness V1과 Harness V3는 모두 구형 comma three, comma threex, comma four 기기와 호환됩니다. 단, comma three 기기에서 오래된 openpilot 버전이나 openpilot 기반 fork를 실행하는 경우 Harness V1의 comma power를 요구하므로 Harness V3와 동작하지 않을 수 있습니다.

차량을 바꾸거나 차량 하네스 부분의 일부를 교체하려는 Harness V1 사용자라면, comma.ai 상점에서 구매할 경우 전체 Harness V1을 Harness V3로 교체해야 합니다. comma.ai는 더 이상 Harness V1 하드웨어를 판매하지 않기 때문입니다. 안타깝게도 상점에서 이를 명확히 설명하지 않으므로, 이 부분은 이 문서를 믿어야 합니다. 더 흔한 브랜드 차량이라면 [Mr. One](https://oneclone.net/product/harness/)이나 [Konik.ai](https://konik.ai/shop/?v=0b3b97fa6688) 같은 타사 판매처에서 Harness V1 호환 차량 하네스를 찾을 수도 있습니다.

> [!WARNING]
> **Mr. One 하네스는 배선이 순정 comma.ai V1 하네스와 다를 수 있습니다.**
>
> 일부 Mr. One 하네스, 특히 Mazda 버전은 순정 V1 배선 방식을 따르지 않고 IGN 라인을 12V 전원으로 사용합니다. 이 때문에 차량 점화 상태와 관계없이 하네스 박스가 LKAS 카메라에 계속 전원을 보내게 되고, 주차 중 차량 배터리를 방전시킬 수 있습니다.
>
> Mr. One 하네스를 사용 중이고 이 문제가 발생한다면, 순정 V1 배선과 맞도록 하네스를 다시 배선해야 합니다. 전기 작업 경험이 있는 사람에게는 비교적 단순한 수정이지만, 하네스 배선 차이에 익숙하지 않은 사용자에게는 즉시 알아차리기 어려울 수 있습니다.

위의 깔끔한 사진과 달리, 릴레이 박스 이후의 차량 하네스 부분은 특정 차량에서는 매우 다르게 보일 수 있습니다. 특히 카메라가 아닌 다른 위치에서 가로채는 차량이 그렇습니다. 훨씬 길거나 comma power처럼 보일 수도 있습니다.

하네스에 대한 자세한 내용은 https://github.com/commaai/hardware/ 를 참고하세요.

<a id="common-to-all-comma-devices"></a>
## 모든 comma 기기에 공통

<a id="the-bad-obd-c-cable-case"></a>
### OBD-C 케이블 불량 사례

OBD-C는 comma 하네스 박스와 comma 기기 사이에 OBD-C 케이블을 사용하는 [comma.ai 표준](https://github.com/commaai/hardware/blob/master/harness/OBD-C.sch.pdf)입니다. comma는 OBD-C 케이블을 생산, 배송, 판매하지만, 일부 USB-C 케이블도 전기적/물리적으로 호환되어 대신 사용할 수 있습니다.

> [!CAUTION]
> **OBD-C는 12V를 출력합니다. 5V가 아닙니다!** 하네스 박스는 OBD-C 포트를 통해 12V를 출력하며, 이는 **정상적이거나 규격을 준수하는 USB-PD 포트가 아닙니다**. 전원 협상을 하지 않고 **연결 즉시 12V를 직접 공급합니다**. 물리적으로 USB-C 커넥터와 비슷하더라도, 일반 USB-C 기기(휴대폰, 태블릿, 노트북 등)를 하네스 박스의 OBD-C 포트에 **절대 연결하지 마세요**. 해당 기기들은 12V가 아니라 5V를 기대하기 때문에, 그렇게 하면 연결된 기기가 **손상되거나 파손됩니다**. OBD-C는 comma 기기와 이 포트에서 12V 입력을 받도록 특별히 설계된 기기에만 호환됩니다.

> [!CAUTION]
> **C3X 사용자: 불량 케이블은 기기를 죽일 수 있습니다!** C3X 기기에서는 손상되었거나 규격을 벗어난 USB-C 케이블이 12V를 데이터 라인에 쇼트시켜 내부 Panda를 영구적으로 태울 수 있습니다. 자세한 내용은 [C3X의 Panda가 타 버린 사례](#the-fried-panda-case-c3x)를 참고하세요.

**예방 조치**:

* OBD-C 케이블의 기계적 마모를 최소화하려면 자석식 또는 quick-release 마운트를 사용하세요.

**증상**:

* 기기가 “[on-road]” 모드로 들어가지 않습니다. 홈 화면에 멈춰 있습니다.

   * [표준](https://github.com/commaai/hardware/blob/master/harness/OBD-C.sch.pdf)에 따르면 IGN 라인은 SBU1과 SBU2의 조합으로 나오며, 둘 중 하나 또는 둘 모두가 OBD-C 케이블을 제대로 통과하지 못하는 것입니다.
* comma의 케이블 대신 케이블 모음에서 무작위 USB-C 케이블을 사용했는데, 그 케이블이 USB 3.1 Gen 2가 아닙니다(예: 원래 케이블이 없거나 고장났기 때문). 기기는 “Vehicle Online”을 표시하지만 “[on-road]” 모드로 전환되지 않습니다.
* openpilot에서 다음을 포함하되 이에 한정되지 않는 무작위 오류가 발생합니다.
  * “Harness Relay Malfunction”
  * “Check Hardware”
  * “Car Unrecognized”
  * “CAN Bus Error”
  * “CAN Bus Disconnected”
* 케이블에 갈라짐 같은 눈에 보이는 손상이 있습니다.
* USB-C 케이블 테스터로 봤을 때 빠진 선이나 끊어진 선 같은 눈에 보이지 않는 손상이 있습니다.
  * **이 진단에는 반드시 _단순한_ USB-C 케이블 테스터를 사용해야 합니다. 예외는 없습니다.**
  * Amazon을 이용할 수 있다면, 간단한 USB-C 케이블 테스터는 comma support가 답변하기보다 더 빨리 배송되어 도착할 것입니다. 아직 없다면 지금 구하세요. https://amzn.to/40hvt5D
* **전원 문제는 보통 OBD-C 케이블 불량 사례가 아닙니다.** 전원과 GND에는 4쌍의 중복 라인/선이 있기 때문입니다. 물론 일부 쌍이 끊어졌을 수는 있지만, 그 케이블은 그래도 비교적 양호하고 사용 가능한 것으로 볼 수 있습니다. 다만 기기 전원이 켜지지 않는다면 [퓨즈가 나간 사례](#the-blown-fuse-case)일 가능성이 큽니다.
  * Blown Fuse Case는 이 마모와 관련이 없거나 우연히 같이 발생했을 수 있습니다. 자세한 내용은 [퓨즈가 나간 사례](#the-blown-fuse-case)를 참고하세요.
* 차량 퓨즈가 나갔습니다. 전원과 GND에 4쌍의 중복 라인/선이 있다는 점은 좋지만, 반대로 이 라인들이 쇼트될 가능성도 커집니다. 교차 배선을 확인하려면 테스터에 노출된 패드와 멀티미터를 사용해야 합니다.

OBD-C 케이블에 눈에 보이는 손상과 보이지 않는 손상이 있는지 확인하세요. 아래 이미지에서 USB-C의 `TX2+`는 OBD-C에서 `CAN2_H`이며, 이 선이 끊어져 있습니다. 케이블은 겉보기에는 멀쩡해 보입니다.

![PXL_20250625_151254911 MP](https://github.com/user-attachments/assets/362e359f-d6f4-4b57-9d16-7e08e475b7e5)

아래는 Nabeel이 제공한 손상 시연 영상입니다. Nabeel의 사례는 케이블을 약간 움직였을 때만 나타났는데, 차량에서는 이런 상황이 매우 흔합니다.

https://www.youtube.com/watch?v=2NPTUW2f6Os

아래 이미지는 adenta가 기증한 케이블에서 나온 것으로, 외피가 갈라져 있지만 필요한 모든 선은 연결되어 있습니다. **진단을 위해서는 반드시 _단순한_ USB-C 케이블 테스터로 테스트해야 합니다.**

![PXL_20250625_062251389](https://github.com/user-attachments/assets/116f6aa9-764d-403f-a573-61fd4d73540b)

OBD-C 케이블 pinout: https://github.com/commaai/hardware/blob/master/harness/OBD-C.sch.pdf

거의 모든 핀은 연결되어 있어야 합니다. 가끔 사람들이 자기 케이블 모음에서 케이블을 가져와 쓰는데, 작동하지 않는다면 보통 선/핀이 빠져 있기 때문입니다. OBD-C 케이블의 데이터 라인에는 중복성이 많지 않으므로, 일부가 손상되었거나 불완전하면 comma 기기가 제대로 작동하지 않습니다. 선도 매우 작고 가늘습니다. USB-C는 더 관대해서 성공적으로 낮은 모드로 동작할 수도 있지만, OBD-C는 덜 관대하고 그렇게 할 수 없습니다.

간단하고 저렴한 USB-C 케이블 테스터(스마트 기능 없이 핀만 테스트하며, 실제 기기에 절대 꽂지 말라는 경고를 반드시 따르세요):

* https://amzn.to/40hvt5D
  * Amazon을 이용할 수 있다면, 간단한 USB-C 케이블 테스터는 comma support가 답변하기보다 더 빨리 배송되어 도착할 것입니다. 아직 없다면 지금 구하세요.
* https://caberqu.com/home/20-42-c2c-caberqu-746052578813.html#/26-with_or_without_case-without_case - 위 Nabeel 영상에 나온 제품입니다.

comma four의 경우 comma는 곧고 더 얇은 새 케이블을 만들었습니다. 어떤 사람들은 곧은 케이블을 좋아하지 않고 스트레스를 줄이기 위해 각진 케이블을 선호하므로, 그 해결책은 아래 “Erich의 추천”을 보세요. 또한 comma가 새로 만든 케이블은 OBD-C 표준에서 사용하지 않는 `D+`와 `D-` 라인이 없어서 조금 더 얇아졌습니다. 이 라인들이 없으므로 12V에 쇼트될 수 없고, [C3X의 Panda가 타 버린 사례](#the-fried-panda-case-c3x) 같은 문제를 방지합니다.

USB-C 케이블 테스터를 사용할 때, comma four OBD-C 케이블에서는 `D+`와 `D-` 라인이 연결되어 있지 않은 것이 정상입니다.

![USB 테스터에 꽂힌 comma four 케이블, D+와 D- 라인이 없음](https://github.com/user-attachments/assets/440de012-f9e0-4ab7-bdee-f520ad45fc24)

위 이미지는 Erich의 “Comma 4 unleashed” 영상에서 가져온 것입니다: https://youtu.be/_dNvrqM1688?t=1905

**해결 방법**:

* 케이블 자체가 손상되었다고 가정하기 전에 [OBD-C 케이블이 하네스 박스에 완전히 꽂히지 않은 사례](#the-not-fully-inserted-obd-c-cable-into-harness-box-case)를 확인하세요. 멀쩡한 케이블도 하네스 박스에 끝까지 들어가지 않았을 뿐인데 훨씬 심각한 문제처럼 보일 수 있습니다.
* 빠르고 임시적인 방법은 OBD-C 케이블을 뒤집어 보는 것입니다. 영구적인 해결책은 아닐 수 있지만, 기기를 다시 작동시키는 데 도움이 될 수 있습니다. 물론 무엇이 어떻게 고장났는지에 따라 충분하지 않을 수도 있습니다.
* OBD-C 케이블이 손상되었다면 새 케이블로 교체하세요. comma three 기기에 사용되는 OBD-C 케이블은 긴 각진 목을 가진 특수 케이블이라, comma three 기기의 움푹 들어간 포트에 꽂을 수 있습니다. 가장 잘 맞고 카메라를 가리지 않게 하려면 comma three 기기용으로 특별히 설계된 케이블을 사용해야 합니다.
  * 교체용 OBD-C 케이블을 구할 수 없지만 급히 필요하다면, USB 3.1 Gen 2 이상 케이블(Thunderbolt 3 또는 4)을 임시 대체품으로 사용할 수 있습니다. 이런 케이블은 대형 매장이나 온라인에서 찾을 수 있습니다. 각진 목은 없으므로 그동안 comma나 Mr. One에서 주문해 두세요.
    * Best Buy: https://www.bestbuy.com/product/insignia-3-3-usb-c-to-usb-c-3-2-gen-2-superspeed-10gbps-cable-black/J2FPJKSZGR - Best Buy의 자체 브랜드인 Insignia는 매장에서 바로 구해야 할 때 좋은 선택지입니다.
    * Wal-Mart: 안타깝게도 호환 케이블을 매장에 비치하지 않는 것으로 보입니다.
  * 기존 케이블과 각진 어댑터 세트를 함께 사용할 수도 있습니다: https://amzn.to/3TcV389
  * **comma four (C4) 사용자**:
    순정 C4 케이블은 양쪽이 모두 곧은 형태이므로, 각진 연결을 원할 수 있습니다. Erich는 순정 케이블과 함께 사용할 때 [이 특정 각진 USB-C 연장 케이블](https://amzn.to/4oYG6DS)이 잘 작동한다고 확인했습니다.
* OBD-C 케이블 설치가 눌려 있다면, USB 3.1 Gen 2 연장 케이블을 사용해 커버 아래에서 눌리지 않도록 배선할 수 있습니다.
  * https://amzn.to/4n7BZ8V
    * 이 제품에는 여러 변형이 있습니다.
  * https://amzn.to/3ZI82lR
    * 이 제품에는 on-off 스위치가 있습니다!
* 기기를 자주 제거한다면, OBD-C 케이블링의 기계적 마모를 줄이기 위해 OBD-C용으로 만들어진 자석식 또는 quick-release 마운트를 사용하는 것을 고려하세요. [comma.ai Discord](https://discord.comma.ai)의 #hw-unofficial을 참고하세요.
* USB-C 케이블 테스터로 검사했을 때 케이블이 양호하다면, 문제가 차량 하네스에 있을 수 있으므로 [차량 하네스 불량 사례](#the-bad-car-harness-case)와 [OBD-C 포트 불량 사례](#the-bad-obd-c-port-case)를 확인하세요.
* comma four와 comma four 케이블 조합인가요? [케이블이 끝까지 꽂히지 않은 사례 (C4)](#the-cable-not-plugged-in-all-the-way-case-c4)도 확인하세요.

**판매처**:

* comma.ai: https://comma.ai/shop/obd-c-cable
  * [Rivian, Ford, Tesla 같은 브랜드용 긴 케이블 버전도 요즘은 TPU를 사용합니다.](https://discord.com/channels/469524606043160576/954493346250887168/1390435764772409495)
* Mr. One: https://oneclone.net/product/obd-c-cable-for-c3/
* Konik.ai: https://konik.ai/shop/usb-c-cable/ - Konik.ai의 케이블은 comma 및 Mr. One 케이블과 물리적으로 다르며, 움푹 들어간 포트가 없는 자체 하드웨어 클론용입니다. 하지만 내부적으로 특별한 것은 아니므로, Amazon이나 현지에서 호환되는 것을 구하는 것도 고려하세요.

**예시**:

* [Nabeel의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1383173273466179727)
  * https://www.youtube.com/watch?v=2NPTUW2f6Os
* [0pointjd의 C3](https://discord.com/channels/469524606043160576/524592892627517450/1330161284049535036)
* [thinkpad4by3의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1419877307807699017)
  * GND 핀/선이 끊어져 있었습니다. 케이블을 흔들면 일시적으로 작동했습니다. [퓨즈가 나간 사례](#the-blown-fuse-case)의 관련 항목을 보세요.
* [johntthesmith의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1433136778721628261)
  * 하네스까지 교체했지만, 먼저 케이블을 테스트했어야 했던 사례입니다.
* [jimmyjam_50066의 C4](https://discord.com/channels/469524606043160576/1436852432503046294/1465545774162251836)
  * 테스터를 돌렸고, CC2/CC1(USB 용어 기준), SBU1 또는 SBU2(OBD-C), 혹은 D+/D- 라인 옆 핀이 누락되었거나 약했습니다.
  * 알려진 첫 번째 불량 C4 케이블 사례입니다.

<a id="the-not-fully-inserted-obd-c-cable-into-harness-box-case"></a>
### OBD-C 케이블이 하네스 박스에 완전히 꽂히지 않은 사례

때로는 OBD-C 케이블 자체는 괜찮지만, 하네스 박스에 완전히 끼워지지 않았을 뿐입니다. 케이블이 작동할 만큼 충분히 꽂힌 것처럼 보여도 이런 일이 생길 수 있고, [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case), [차량 하네스 불량 사례](#the-bad-car-harness-case), 심지어 [OBD-C 포트 불량 사례](#the-bad-obd-c-port-case)처럼 보일 수 있습니다.

**증상**:

* 기기가 “[on-road]” 모드로 들어가지 않습니다. 홈 화면에 멈춰 있습니다.
* openpilot에서 다음을 포함하되 이에 한정되지 않는 무작위 오류가 발생합니다.
  * “Harness Relay Malfunction”
  * “Check Hardware”
  * “Car Unrecognized”
  * “CAN Bus Error”
  * “CAN Bus Disconnected”
* 케이블이 하네스 박스에 절반 정도만 들어가는 것처럼 보입니다.
* 하네스 박스 쪽 케이블이 헐겁거나 불안정하게 느껴집니다.
* 동작이 간헐적이며, 최종적인 해결책보다 더 심각한 문제처럼 보입니다.

**해결 방법**:

* OBD-C 케이블을 하네스 박스에 단단히 다시 꽂고, 실제로 완전히 삽입되었는지 확인하세요.
* “대충 들어갔으니 괜찮다”고 가정하지 마세요. 케이블이 연결된 것처럼 보이더라도, 제대로 접촉할 만큼 깊게 들어가지 않았을 수 있습니다.
* comma four에서 작업 중이라면, 기기 쪽 체결 문제를 문서화한 [케이블이 끝까지 꽂히지 않은 사례 (C4)](#the-cable-not-plugged-in-all-the-way-case-c4)도 확인하세요.
* 케이블이 완전히 들어갔는데도 문제가 계속된다면, [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)로 넘어가 하네스나 포트 진단으로 확대하기 전에 단순 USB-C 케이블 테스터로 테스트하세요.

<img width="648" height="800" alt="Image" src="https://github.com/user-attachments/assets/4e55e1fb-fc48-428a-aad6-e0a8476baa51" />

[이미지는 Discord의 subzeroalphaq가 제공했습니다.](https://discord.com/channels/469524606043160576/1436852432503046294/1484461433289838736)

**예시**:

* [Saberion의 C4](https://discord.com/channels/469524606043160576/1436852432503046294/1484518779374272512)
  * 순정 comma four 케이블이 Bosch C 하네스에 절반 정도만 들어가는 것이 정상인지 질문했습니다.
* [janxman.의 C4](https://discord.com/channels/469524606043160576/524592892627517450/1496206614313697380)
  * 조금 더 힘을 줘서 코드를 하네스 끝까지 밀어 넣는 것이 해결책이었다고 확인했습니다.
  * 완전히 들어가자 기기가 calibration percentage를 표시하기 시작했습니다.

<a id="the-bad-obd-c-port-case"></a>
### OBD-C 포트 불량 사례

이 사례는 위 사례보다 훨씬 심각하며, 쉽고/또는 신뢰할 수 있는 해결책은 실제로 없습니다. 완전성을 위해 여기에 문서화합니다. 기술이 있고 [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case) 및/또는 [차량 하네스 불량 사례](#the-bad-car-harness-case)를 배제했다면 이 부분을 볼 수 있지만, 여기서 포기해도 탓하지 않겠습니다.

**예방 조치**:

* OBD-C 포트의 기계적 마모를 최소화하려면 자석식 또는 quick-release 마운트를 사용하세요.
* C4: 순정 C4 케이블은 양쪽이 모두 곧은 형태이므로, 각진 연결을 원할 수 있습니다. Erich는 순정 케이블과 함께 사용할 때 [이 특정 각진 USB-C 연장 케이블](https://amzn.to/4oYG6DS)이 잘 작동한다고 확인했습니다. 어떤 사람들은 카메라에 너무 가깝게 설치해 케이블과 포트에 계속 압력이 걸리게 합니다.

**증상**:

증상은 전반적으로 [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)와 매우 비슷하지만, 문제는 케이블이 아니라 OBD-C 포트 자체에 있습니다.

* OBD-C 포트가 물리적으로 손상되었습니다.
* [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)와 [차량 하네스 불량 사례](#the-bad-car-harness-case)를 배제했습니다.
* 기기가 “[on-road]” 모드로 들어가지 않습니다. 홈 화면에 멈춰 있습니다.
* openpilot에서 다음을 포함하되 이에 한정되지 않는 무작위 오류가 발생합니다.
  * “Car Unrecognized”
  * “CAN Bus Error”
  * “CAN Bus Disconnected”

**해결 방법**:

할 줄 아는 사람이라면 알고 있을 것입니다.

[안타깝게도 reflow가 아주 잠깐의 시간만 벌어 준다는 일화가 있는 듯합니다.](https://discord.com/channels/469524606043160576/954493346250887168/1302002657937854556)

**예시**:

사례는 드문 편이고, 후속 내용이 공개적으로 공유되지 않았습니다. 추가하고 싶은 사례가 있다면 pull request나 issue로 추가해 주세요.

* C2
  * [defy의 c2](https://discord.com/channels/469524606043160576/954493346250887168/1302031683284893840)
* C3
  * [minty의 c3](https://discord.com/channels/469524606043160576/1121848816870641775/1124891817566023680)
* C4
  * [bigboy382938의 C4 (아직 고장나지는 않았지만... 헐거움)](https://discord.com/channels/469524606043160576/1436852432503046294/1466453620458262528)

**자료**:

* USB-C/OBD-C 포트 수리 분해 part 1: https://www.youtube.com/live/TE757kH3EMM
* USB-C/OBD-C 포트 수리 분해 part 2: https://www.youtube.com/live/gTw_Qq8scqo

<a id="the-bad-car-harness-case"></a>
### 차량 하네스 불량 사례

comma 기기는 OBD-C 케이블을 통해 [comma.ai 하네스](#commaai-harness)를 거쳐 차량에 연결됩니다.

안타깝게도 하네스가 고장날 수 있으며, 특히 릴레이 박스 안에 물리 릴레이를 사용하는 V1 하네스에서 그렇습니다.

사용 중인 하네스를 식별하려면 [comma.ai 하네스에 대한 로컬 분류 섹션](#commaai-harness)을 참고하세요.

**증상**:

* 기기 전원이 켜지지 않습니다.
* OBD-C 케이블이 양호하다고 알려져 있거나 최근 교체되었습니다. 즉, [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)와 [OBD-C 케이블이 하네스 박스에 완전히 꽂히지 않은 사례](#the-not-fully-inserted-obd-c-cable-into-harness-box-case)가 배제되었습니다. 이 작업을 먼저 하세요.
* openpilot에서 다음을 포함하되 이에 한정되지 않는 무작위 오류가 발생합니다.
  * “Car Unrecognized”
  * “CAN Bus Error”
  * “CAN Bus Disconnected”
  * “Harness Relay Malfunction”
  * “Check Hardware”
* 릴레이 박스나 하네스 주변에서 이상한 소리가 들립니다. 물론 무엇이 “이상한”지는 다를 수 있습니다. 정상적인 V1 하네스는 기기 전원이 켜지고 꺼질 때 클릭 소리가 나지만, 지속적인 클릭이나 윙윙거림이 들린다면 정상은 아닙니다.

**해결 방법**:

* _아래 단계는 하드웨어 비용을 아끼는 쪽에 가깝습니다. 시간이 중요하다면 그냥 건너뛰고 comma에서 [complete car harness](https://comma.ai/shop/car-harness)를 구매해 교체 테스트를 해도 됩니다. 최악의 경우, 문제가 아니었다면 하드웨어를 반품하는 배송비(미국 기준 약 $10)만 부담하면 됩니다._
* [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)와 [OBD-C 케이블이 하네스 박스에 완전히 꽂히지 않은 사례](#the-not-fully-inserted-obd-c-cable-into-harness-box-case)를 배제하세요. 먼저 확인하기 쉽고 저렴합니다.
* 차량 자체 퓨즈를 확인하세요. 차량 퓨즈가 나가면 comma 기기에 전원이 들어오지 않을 수 있습니다.
* 사용 중인 하네스 revision이 V1인지 V3인지 식별하세요.
* 멀티미터의 continuity test를 사용해, 차량별 하네스 커넥터의 pinout을 https://github.com/commaai/hardware/tree/master/harness 와 대조하세요.
  * 이 부분이 불량이면 [차량별 하네스 커넥터](https://comma.ai/shop/harness-connector)를 수리하거나 교체하세요.
* Harness V1: 차량별 하네스 커넥터가 정상임을 테스트한 뒤, 현재 실제로 테스트할 수 있는 유일한 방법은 comma에서 [complete car harness](https://comma.ai/shop/car-harness)를 구매해 교체하는 것입니다. 문제가 아니라면 새 하드웨어를 [반품](https://shop.comma.ai/a/returns)할 수 있습니다.
  * 안타깝게도 comma는 더 이상 V1 하네스 하드웨어를 판매하지 않으므로, 이 해결책을 위해 complete Harness V3 car harness를 시도/구매해야 합니다.
* Harness V3: 차량별 하네스 커넥터가 정상임을 테스트한 뒤, 현재 실제로 테스트할 수 있는 유일한 방법은 comma에서 [새 harness relay box](https://comma.ai/shop/harness-box)를 구매해 교체하는 것입니다. 문제가 아니라면 새 하드웨어를 [반품](https://shop.comma.ai/a/returns)할 수 있습니다.
  * rattail98의 사례처럼, 문제는 하네스 박스 내부 저항 고장일 수 있고, 전자 수리 기술이 있는 사람이라면 교체할 수 있습니다. 자세한 내용은 [harness box v3 회로도](https://github.com/commaai/hardware/blob/master/harness/v3/Harness_Box.pdf)를 보세요.
* 새 하네스를 차량에서 테스트하세요.

바라건대 그것이 문제이고, 문제가 해결되기를 바랍니다.

**예시**:

- [wakywayne의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1397560030256955533)
  - OBD-C 케이블도 교체했지만, V1에서 V3로 complete harness를 교체할 때까지 문제가 계속되었습니다.
- [Yan의 C3](https://github.com/commaai/openpilot/issues/32179#issuecomment-2053766029)
  - 직접 만나 하드웨어를 교체하고 바꿔 보았습니다. comma support가 보증으로 relay box를 교체하게 하는 데 많은 설득이 필요했습니다. 이는 V1 하네스에서 V1 하네스로 교체한 사례였습니다.
- [rattail98의 C3X](https://discord.com/channels/469524606043160576/524592892627517450/1399544048879927418)
  - 철저히 디버깅해 V3 relay box만의 문제로 좁혔습니다.
  - [처음에는 support를 통해 V3 relay box, harness, OBD-C cable을 교체했지만](https://discord.com/channels/469524606043160576/524592892627517450/1403142981489528993), [문제는 계속되었습니다](https://discord.com/channels/469524606043160576/524592892627517450/1403416357004906701).
  - [추가 디버깅과 OBD-C cable 및 Subaru A harness 교체 후](https://discord.com/channels/469524606043160576/524592892627517450/1415049990870405140), 문제는 harness box로 좁혀졌습니다.
  - harness box를 검사한 결과, R4 저항이 고장나 continuity가 나오지 않았습니다.
  - 고장난 1k ohm 저항을 2.2k ohm 저항으로 교체해 향후 고장을 방지했습니다. 이로써 문제가 해결되었습니다.
  - IGN line의 voltage spike가 저항 고장을 일으켰을 가능성이 의심되며, 차량의 이전 전면부 손상과 수리 때문일 수 있습니다.
  - harness box는 접착제 아래 숨겨진 나사 하나로 고정되어 있습니다.

<a id="the-bad-ir-blaster-case"></a>
### IR 블래스터 불량 사례

**증상**:

* 해가 진 뒤 기기가 주의를 기울이라고 소리칩니다.
* 필터가 없거나 약한 휴대폰 카메라로 보면 IR blaster가 작동하지 않는 것이 보입니다.

**해결 방법**:

이는 우회 방법이지 수리는 아닙니다. 제대로 된 수리는 IR LED를 수리하는 것이겠지만, 이 섹션의 세부 내용은 _TODO_ 입니다. 더 제대로 된 수리 방법이 있다면 알려 주세요.

아래 지침은 우회 방법입니다.

* 보안 카메라용 IR blaster를 구매해 steering column에 장착합니다.
 * 예: https://amzn.to/3WomsWm
* 차량의 12V 시스템에 꽂은 12V 어댑터로 전원을 공급합니다.

**예시**:

* [Ry의 C3X](https://discord.com/channels/469524606043160576/905950538816978974/1431553007555711101)
  * 우회 방법.

<a id="the-running-too-old-of-an-os-case"></a>
### 너무 오래된 OS를 실행 중인 사례

comma.ai는 자사 하드웨어에서 최신 `release-*`, `nightly`, 그리고 특정 WIP 브랜치의 comma openpilot만 지원합니다. 그리고 이런 브랜치들은 기기에 비교적 최신이거나 가장 최신인 OS가 설치되도록 합니다. fork는 다른 OS 버전을 설치할 수 있습니다.

comma.ai는 신뢰성, 공급망, 비용 절감 및 기타 이유로 때때로 하드웨어를 “진화”시킵니다. 이는 하드웨어가 오래된 openpilot 및 OS 버전과 호환되지 않을 수 있다는 뜻입니다. 이를 대비해 comma는 새 하드웨어를 지원하도록 OS와 openpilot 브랜치를 업데이트합니다. 더 최신 OS가 필요할 수 있는 하드웨어 변경에 대한 자세한 내용은 [comma three (C3)](#comma-three-c3)와 [comma threex (C3X)](#comma-threex-c3x)의 “Evolutions” 섹션을 참고하세요.

fork, 오래된 브랜치, 그리고 openpilot 또는 다양한 fork 설치를 설명하는 YouTube 안내는 성격상 기반이 되는 최신 OS와 openpilot 버전을 따라가지 못할 수 있습니다.

안타깝게도 comma는 설치 과정에서 호환되지 않는 OS 또는 openpilot 버전 설치를 감지하고 차단할 방법을 제공하지 않습니다. comma의 관점은 release 및 nightly 브랜치를 벗어난다면 사용자가 고급 사용자이며 자신이 무엇을 하는지 알아야 한다는 것입니다. 또한 최신이 아니거나, 최신으로 유지될 수 없거나, YouTube 영상처럼 접근성은 좋지만 여전히 오래된 문서와 지침이 많이 있다는 점도 안타깝습니다. 뭐, 세상은 완벽하지 않습니다.

**증상**:

본질적으로 정의가 매우 불명확하고 이 섹션도 불완전하기 때문에 증상은 매우 다양할 수 있습니다.

* 방금 comma.ai에서 기기를 [“수리”](https://comma.ai/shop/comma-3x-out-of-warranty-repair)받았습니다. 실제로는 새로 조립된 기기를 보내주는 것입니다.
* 몇 분 동안 실행되다가 화면이 멈추고 기기가 reset됩니다.
  * 예: Wi-Fi driver가 오래됨
* 어떤 때는 화면이 완전히 보이고 밝기도 좋지만, 다른 때는 밝기가 매우 어두워 화면이 거의 보이지 않습니다.
  * 예: sensor driver가 오래됨
* 기기가 과열됩니다.
  * 예: fan control driver가 오래됨
* 대부분의 openpilot 배포판이나 openpilot fork는 보통 auto-update됩니다. 그렇기는 해도, 어떤 이유로 auto-update가 작동하지 않았거나 비활성화되어 구형 하드웨어 revision에서 오래된 OS와 함께 오래된 openpilot을 쓰는 경우는 보통 바로 무너지지는 않습니다. 그래도 수정 사항을 위해 업데이트하고 싶을 수 있습니다.

**해결 방법**:

호환되는 OS를 설치하는 openpilot codebase를 실행해야 합니다.

* 부팅 중 화면을 마구 탭한 뒤 “Uninstall”을 선택해 제거합니다.
* 그렇게 할 수 없다면 [OS가 꼬인 사례](#the-os-is-messed-up-case)를 진행하세요.
* 최신 comma openpilot을 설치합니다.
* fork를 반드시 사용해야 한다면 아래 팁을 보세요.

> [!TIP]
>
> **일부 인기 fork의 현재 알려진 상태**:
>
> 마지막 업데이트: 2025년 7월
>
> 이 문서는 살아 있는 문서입니다. 최신 상태는 각 커뮤니티에서 확인하고, 가능하다면 이 섹션 업데이트를 도와주세요.
>
> * sunnypilot - `release-c3`를 설치하지 말고 `staging-c3-new`를 설치하세요.
> * frogpilot - 괜찮을 것입니다. OS 변경 사항을 fork의 OS에 backport했습니다.

* 최신이 아닌 YouTube 영상과 지침을 주의하세요. YouTube 영상은 업데이트할 수 없습니다.
  * YouTube 영상에서 이곳까지 왔다면, 영상 작성자에게 연락해 최신 지침을 담은 댓글을 영상 상단에 고정해 달라고 요청하세요.
  * 이 문제가 있는 영상:
    * [Comma 3X OpenPilot & SunnyPilot Install - 2024 Kia EV6 GT
](https://www.youtube.com/watch?v=YhYEYcfNL5o)
* 마지막으로 fork 사용자는 자신이 사용하는 fork의 _문서화된_ 안내를 확인해야 합니다. YouTube 영상이나 대체 지침은 최신이 아닐 수 있고, 최신 OS 또는 openpilot 버전과 작동하지 않을 수 있습니다. 그래도 문서화된 안내를 보완하는 자료로는 여전히 훌륭할 수 있습니다.

**예시**:

* [Magnetar의 C3X](https://discord.com/channels/469524606043160576/524592892627517450/1398669054809608345)
   * “이미 factory reset과 재설치 등 모든 것을 시도했습니다. 몇 초에서 최대 약 5분 정도는 잘 작동합니다. 그러다가 화면이 몇 초 동안 멈추고 comma 로고와 함께 reboot됩니다.”
 * [/u/Unable-Grape2361의 C3X](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comma_3x_recovery_mechanism_after_overheating/)
   * “안타깝게도 교체품은 원래 기기에서는 전혀 없었던 과열 문제에 시달리고 있습니다.”

<a id="common-to-all-comma-two-family-devices"></a>
## 모든 comma two 계열 기기에 공통

comma two 계열은 comma 하드웨어의 2세대입니다. 배터리를 제거하고, thermal solution을 채워 넣고, 전면 카메라를 IR filter가 없는 변형으로 교체한 수정 Leeco Le Pro 3를 기반으로 합니다. 또한 CAN 통신, 팬 지원, 배터리 에뮬레이션과 bootkick 같은 휴대폰 하드웨어를 속이기 위한 하드웨어/소프트웨어 해킹을 지원하는 통합 comma panda PCB가 들어 있습니다.

> [!NOTE]
> 이 커뮤니티에 처음 들어오는 중이라면 comma threex 또는 비슷한 기기를 구하는 것이 좋습니다. openpilot 주변 커뮤니티는 지속적인 지원과 현재 개발을 위해 comma threex 계열 기기로 이동했기 때문입니다.

> [!NOTE]
> 안타깝게도 이 섹션은 아직 작성되어야 합니다. 추가하고 싶은 사례가 있다면 pull request나 issue로 추가해 주세요. 지금은 [comma Discord](https://discord.comma.ai)의 #hw-two-eon 채널을 검색해야 합니다.

<a id="the-cant-proceed-to-installation-because-wi-fi-cant-connect-to-internet-case-on-my-comma-two"></a>
### comma two에서 Wi-Fi가 인터넷에 연결되지 않아 설치를 진행할 수 없는 사례

![이미지](https://github.com/user-attachments/assets/8f1e1e07-e359-421f-b399-5c0a46b61538)

**증상**:

* comma two 기기에서 Wi-Fi를 설정한 뒤 인터넷 연결에 실패하고, 그 때문에 진행이 막힙니다.

**해결 방법**:

* 컴퓨터에서 https://github.com/ophwug/c2-neos-alt-fix-install 를 사용합니다.
* 위 방법이 작동하지 않으면 https://github.com/jyoung8607/neos-manual-install 의 지침을 따르세요.

<a id="common-to-all-comma-three-family-devices"></a>
## 모든 comma three 계열 기기에 공통

comma three 계열은 comma 하드웨어의 3세대이며, comma.ai가 처음부터 직접 설계한 첫 세대입니다.

<a id="the-build-error-on-boot-case"></a>
### 부팅 시 빌드 오류 사례

**증상**:

* 부팅 시 어떤 형태로든 build error가 발생합니다.

![이미지](https://github.com/user-attachments/assets/6bd09b68-c379-4451-802b-05ad57fcf9bb)

**해결 방법**:

comma의 브랜치나 fork에서 이런 일이 발생할 수 있습니다. 부팅 중 화면을 마구 탭한 뒤 “Reset”을 선택해 reset을 시도하세요. openpilot을 다시 설치하세요.

<a id="the-os-is-messed-up-case"></a>
### OS가 꼬인 사례

**증상**:

* 기기가 부팅되지 않는 것 같거나, 어떤 이유로든 멈춥니다.
* 부팅 중 화면을 마구 탭한 뒤 “Reset”을 선택해도 기기가 factory state로 돌아가지 않습니다.

**해결 방법**:

https://flash.comma.ai/ 로 reflash하세요.

https://flash.comma.ai 가 때때로 작동하지 않을 수 있습니다. 그럴 때는 C3 clone 제작자인 Mr. One의 Windows 전용 Qualcomm 소프트웨어 대안을 사용해 보세요.

https://mr-one.cn/?post=24

Archive: https://web.archive.org/web/20250520040523/https://mr-one.cn/?post=24

<a id="the-blown-fuse-case"></a>
### 퓨즈가 나간 사례

_Blown Fuse Case라는 이름은 약간 잘못된 표현일 수 있습니다. 해당 퓨즈는 self-resetting이어야 하지만, 제대로 reset되지 못하거나 예상과 다르게 동작할 수 있습니다. 이 이름은 역사적 이유, 링크, 보관 목적 때문에 유지합니다._

**증상**:

> [!IMPORTANT]
> 퓨즈가 나갔다고 가정하기 전에 다른 **생명 징후**를 확인하는 것이 매우 중요합니다. 화면이 죽은 기기는 전원이 켜지지 않는 기기로 오해되기 쉽습니다. 팬 소리, 깜빡이는 불빛, 기기가 engage되는지 같은 확인해야 할 증상은 [화면이 작동하지 않거나 죽어 가는 사례](#the-screen-doesnt-work-or-is-dying-case)를 참고하세요.

* 연결했을 때 기기 전원이 켜지지 않습니다.
* 기기가 켜진 상태를 유지하지 못합니다.
* 기기 전원이 켜지지만 loading 중에 꺼지거나 black screen이 됩니다.
* self-resetting fuse의 저항이 높은 값에 고정됩니다. 예를 들어 datasheet 기준으로 많아도 약 0.02 ohm이어야 하는데 0.3~43 ohm이 나오는 경우입니다. 0.3 ohm은 일부 문제 있는 기기에서 관찰된 값일 뿐이며, 기술적으로는 0.02 ohm을 넘으면 spec을 벗어납니다.
* 퓨즈에 heat gun을 대면 저항이 나쁜 수준까지 올라갑니다.
* (V1 harness) 부팅 실패 시 relay box를 흔들면 마라카스 같은 소리가 납니다.
* 전원이 켜진 상태에서 퓨즈 양단에 큰 voltage drop이 있습니다. 자세한 내용은 아래 dazoe 사례를 보세요.
* 뒤쪽 파란 불은 여전히 깜빡일 수 있습니다.
* https://flash.comma.ai 로 flashing할 때 connection lost 화면과 함께 실패하는 경우가 있습니다.

**원인**:

* 왜 이런 일이 발생하는지 정확히 알지는 못하지만, 하드웨어는 전반적으로 automotive use case에 정확히 맞는 spec의 부품만으로 구성되어 있지는 않습니다.
* 자동차 같은 환경의 하드웨어는 datasheet에 적힌 퓨즈의 지정 동작 온도보다 훨씬 높은 온도에서 동작할 수 있다는 점은 알고 있습니다. 직사광선을 받는 차량 내부에서는 85C와 125C 차이가 생길 수 있습니다. 이로 인해 퓨즈가 시간이 지나며 열화되고 결국 고장날 수 있습니다.
* 차량의 12V 시스템은 보통 14V 이상에서 동작하는데, 이는 datasheet에 적힌 퓨즈의 12V max rating보다 높습니다. 이 역시 퓨즈를 시간이 지나며 열화시키고 결국 고장나게 할 수 있습니다.
  * [OEM automotive electronics design에 관여하는 Le_Potato와의 대화 (OPC)](https://discord.com/channels/771493367246094347/771493367779295304/1425279455609360487)
* 아래 해결 방법 섹션에서는 끊어진 퓨즈를 교체할 OEM 퓨즈를 지정합니다. OEM 퓨즈 대신 automotive-grade 퓨즈를 사용할 수 있는지는 아직 알 수 없는 미스터리입니다. 납땜 blob은 해당하지 않습니다 😂. 실제로 시도한다면 결과를 커뮤니티에 알려 주세요.

**진단**:

우리가 보고 있는 부품은 self-reset이 가능해야 하지만, 어떤 이유로든 그렇게 하지 못합니다.

이 부품은 OBD-C 포트 근처, 그리고 기기의 주 처리 장치인 SOM(System-On-Module) 보드 아래에 있습니다. heatsink를 제거하기 전까지는 바로 보이지 않을 수 있으며, 접근하려면 heatsink를 제거해야 합니다.

아래 이미지에서는 초록색으로 동그라미 표시되어 있습니다. 근처에는 다른 색으로 동그라미 표시된 부품도 있는데, 보유한 하드웨어 revision에 따라 있을 수도 있고 없을 수도 있는 다른 퓨즈일 수 있습니다.

C3:

![OBD-C 포트와 SOM 근처, 제거해야 하는 heatsink 아래에 초록색으로 표시된 Blown Fuse. (C3)](https://github.com/user-attachments/assets/af59106f-57d4-4c3f-b993-2731b1ee6e0d)

[이미지는 Discord의 posterduck이 제공했습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1408484686044598505)

C3X:

![OBD-C 포트와 SOM 근처, 제거해야 하는 heatsink 아래에 초록색으로 표시된 Blown Fuse. (C3X)](https://github.com/user-attachments/assets/20ae0654-c34f-4268-a953-cf72975209f4)

[이미지는 Discord의 zum114가 제공했습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1426460252383215658)

존재가 알려진 퓨즈 변형:

* [S12: MF-NSML350/12](https://bourns.com/docs/product-datasheets/mf-nsml-x.pdf?sfvrsn=31b87ef6_12)
* [V12: MF-NSML380/12](https://bourns.com/docs/product-datasheets/mf-nsml-x.pdf?sfvrsn=31b87ef6_12)
* [CT: 1206L350/12SL](https://www.littelfuse.com/products/fuses-overcurrent-protection/polyswitch-resettable-pptc-devices/surface-mount-polyswitch-resettable-pptc-devices/low-rho-smd/1206l350-12sl)

초록색으로 표시된 것뿐 아니라 근처의 파란색/빨간색 부품처럼 이와 비슷한 다른 퓨즈도 있을 수 있습니다. 원한다면 그것들도 교체할 수는 있지만, 실제로는 아마 초록색 하나만 교체하면 됩니다. 나머지는 그대로 두는 것이 좋을 것입니다. 물론 측정해 보는 것은 괜찮습니다.

퓨즈 측정 결과가 양호하지만 short가 있고 C3X라면 [Step-down DC/DC 레귤레이터 불량 사례](#the-bad-step-down-dcdc-regulator-case)를 보세요.


> [!WARNING]
> 퓨즈의 육안 검사는 진단으로 충분하지 않습니다. 퓨즈가 나갔는지 판단하려면 반드시 멀티미터로 퓨즈 저항을 측정해야 합니다.

> [!TIP]
> **멀티미터로 퓨즈 저항 측정하기**
>
> **테스트를 위해 퓨즈를 desolder할 필요는 없습니다.** 이 진단은 기본적인 멀티미터 사용 능력이 있는 사람이라면 누구나 할 수 있습니다. 다만 퓨즈에 접근하려면 기기를 열고 분해해야 합니다.
>
> 멀티미터 사용이 처음인 사람을 위해, 퓨즈 확인 방법은 다음과 같습니다.
>
> 1.  **멀티미터 설정:** 다이얼을 저항 설정으로 돌립니다. 보통 오메가 기호 Ω로 표시됩니다. **정상 퓨즈의 작은 소수 값들을 측정하려면 가능한 가장 낮은 저항 범위(예: 200 Ω)를 선택하는 것이 중요합니다.** 멀티미터가 auto-ranging이 아니고 범위가 너무 높게 설정되어 있으면, 정상 퓨즈에서도 “0”으로 보일 수 있습니다.
> 2.  **리드 저항 측정:** 퓨즈를 테스트하기 전에 멀티미터 probe 끝을 서로 단단히 맞댑니다. 멀티미터는 매우 낮은 저항값(예: 0.1~0.5 Ω)을 표시해야 합니다. 이것이 멀티미터와 리드의 내부 저항입니다. 이 값을 적어 두세요. 대부분의 멀티미터는 이때 beep 소리를 냅니다.
> 3.  **먼저 기기를 데우기:** 테스트 전에 기기를 꽂고 1~2분 정도 동작시켜 퓨즈를 “warm up”하세요. **일부 퓨즈는 차가울 때는 “정상”처럼 읽히지만, 데워진 뒤 실제 불량 상태를 드러내므로 중요합니다.** 데운 뒤 다음 단계로 진행하세요.
> 4.  **기기 전원 끄기:** 부정확한 측정이나 손상을 피하려면 기기가 완전히 꺼져 있고 분리되어 있는지 확인하세요.
> 5.  **퓨즈 측정:** 퓨즈가 보드에 장착된 상태에서 각 probe를 퓨즈 양 끝에 댑니다(in-circuit measurement).
> 6.  **측정값 해석:**
>     *   **정상 퓨즈:** 멀티미터는 매우 낮은 저항을 표시하며, 이상적으로는 2단계에서 측정한 리드 저항과 매우 가까워야 합니다. 2단계에서 멀티미터가 beep 소리를 냈다면 지금도 beep 소리가 나야 합니다.
>     *   **끊어진 퓨즈:** 멀티미터는 높은 저항(예: 0.3~43 Ω) 또는 open circuit(OL 또는 ∞)을 표시하며, 이는 퓨즈가 나갔음을 뜻합니다.
> 7.  **새 퓨즈 측정:** 기기를 분해하고 퓨즈를 교체하기 전에, 새 퓨즈도 측정해 정상 작동하는지 확인하세요.
>
> 퓨즈 자체의 저항을 가장 정확하게 얻으려면 퓨즈 측정값에서 리드 저항(2단계)을 빼는 것을 잊지 마세요.
>
> **고급 진단 참고:** 이 지침은 온도가 올라가거나 부하가 걸릴 때만 실패하는 경우처럼 모든 퓨즈 문제를 다루지는 못할 수 있습니다. 자세한 내용은 아래 예시 섹션의 dazoe 사례를 보세요. dazoe의 C3 진단은 퓨즈 저항을 재는 것보다 조금 더 복잡했고, 더 고급이며 더 위험한 기술이 필요했습니다. 기본적인 멀티미터 사용 능력이 있는 사람이라면 이 진단 자체는 할 수 있지만, 실제 퓨즈 교체는 전문가의 도움이 필요할 수 있습니다. 다만 전자 작업 경험과 올바른 도구가 있다면 DIY로 몇 시간 안에 할 수도 있습니다(아래 참고).

**해결 방법**:

이 문제를 고치려면 나간 self-resetting fuse를 새 것으로 교체해야 합니다. 수리 서비스에 문의하거나, 필요한 기술과 도구가 있다면 DIY 수리를 시도할 수 있습니다.

**수리 서비스**:

* Drago
  * 서비스:
    * 퓨즈 교체 $99
    * 퓨즈가 나갔는지 확실하지 않은 경우 진단비 $30 + 배송비
  * * Discord direct message 링크로 연락(선호): https://discord.com/channels/@me/1412275471479209984
  * Discord DM으로 연락: `awuf`
* 근처에서 board level repair를 할 수 있는 사람이 아래 **DIY 수리** 지침을 따를 수 있습니다. 비용은 경우에 따라 다를 수 있습니다.

**DIY 수리**:

납땜에 익숙하다면 퓨즈를 직접 교체할 수 있습니다.

교체 퓨즈는 Mouser, Digi-Key, Newark 같은 신뢰할 수 있는 전자 부품 판매처에서 찾으세요. 실제 비용은 배송비이므로 여러 개 사 두세요.

*   S12: Bourns `MF-NSML350/12-2` - **Mouser:** https://www.mouser.com/ProductDetail/Bourns/MF-NSML350-12-2?qs=u16ybLDytRaRX65cJT5NUA%3D%3D
*   S12: Bourns `MF-NSML350/12-2` - **Digi-Key:** https://www.digikey.com/en/products/detail/bourns-inc/MF-NSML350-12-2/9859203
*   S12: Bourns `MF-NSML350/12-2` - **Newark:** https://www.newark.com/bourns/mf-nsml350-12-2/ptc-resettable-fuse-12v-1206/dp/72AC9028
*   V12: Bourns `MF-NSML380/12-2` - **Mouser:** https://www.mouser.com/ProductDetail/Bourns/MF-NSML380-12-2?qs=u16ybLDytRZuQwI5f126Qg%3D%3D
*   V12: Bourns `MF-NSML380/12-2` - **Digi-Key:** https://www.digikey.com/en/products/detail/bourns-inc/MF-NSML380-12-2/9859204
*   V12: Bourns `MF-NSML380/12-2` - **Newark:** https://www.newark.com/bourns/mf-nsml380-12-2/pptc-resettable-fuse-3-8a-12v/dp/95AC1557
*   CT: Littelfuse `1206L350/12SLWR` - **Mouser:** https://www.mouser.com/ProductDetail/Littelfuse/1206L350-12SLWR?qs=7MVldsJ5UawvCRT8CTYI7Q%3D%3D
*   CT: Littelfuse `1206L350/12SLWR` - **Digi-Key:** https://www.digikey.com/en/products/detail/littelfuse-inc/1206L350-12SLWR/12807048


**필요한 도구:**
- 저항을 읽을 멀티미터
- 1.3mm 및 1.5mm allen bit/key
- 납땜 인두(매우 가는 팁) + leaded solder
- Desoldering wick(flux 포함)
- 가는 끝의 tweezers
- 기존 퓨즈가 쉽게 떨어지지 않을 경우 작은 cutter가 필요할 수 있음
- 교체 퓨즈 최소 2개(첫 번째를 망가뜨릴 때를 대비). 아래 Vendors 섹션 참고.

**1단계: 분해**

> [!TIP]
> **모든 단계에서 사진을 찍으세요!** 무엇이든 분리하기 전에 connector가 어떻게 놓여 있는지, wire가 어디로 지나가는지, 전체 배치가 어떤지 선명한 사진을 찍으세요. 재조립할 때 모든 것이 정확히 원래 자리로 돌아가도록 하는 데 이 참조 사진들이 매우 중요합니다.

1. **더 쉽게 접근하기 위해 connector 제거:** GPS antenna U.FL connector, GPS JST connector, fan plug, 그리고 heat sink 아래의 다른 U.FL connector를 뽑아 heat sink를 완전히 제거합니다. 이렇게 하면 모든 것에 접근하기가 훨씬 쉬워집니다. 모두 비교적 쉽게 다시 연결될 것입니다.

2. **나사를 조심해서 다루기:** GPS mount의 1.3mm hex screw를 조심하세요. 나사를 풀기 전에 screwdriver bit가 제대로 자리 잡도록 약간의 압력을 주세요. 돌리는 동안 아래로 단단히 누르세요.

3. **heat sink 제거:** 모든 connector를 뽑으면 fuse 영역에 더 잘 접근하기 위해 heat sink를 완전히 제거할 수 있습니다.

**2단계: 퓨즈 교체**

> [!WARNING]
> **교체 퓨즈를 조심해서 다루세요:** tweezers로 퓨즈를 자리 잡게 할 경우 너무 세게 누르지 마세요. 꽤 쉽게 으스러집니다.

1. **desoldering 준비:** **flux가 있는 desoldering wick은 반드시 필요한 도구입니다.** 먼저 기존 퓨즈의 양쪽에 새 solder를 조금씩 더한 뒤 wick으로 제거하세요. 이렇게 하면 열 전달과 제거에 도움이 됩니다.

2. **기존 퓨즈 제거:** 제대로 준비해도 기존 퓨즈가 아주 쉽게 떨어지지 않을 수 있습니다. 어떤 경우에는 위쪽 절반이 먼저 떨어져, 아래쪽 부분을 작은 snip이나 cutter로 조심스럽게 긁어내야 합니다.

3. **pad 청소:** 기존 퓨즈를 완전히 제거한 뒤 pad에 소량의 solder를 더해 주세요(덩어리가 아니라 tinning할 정도로만). 그리고 기존 퓨즈 잔여물이 모두 사라졌는지 확인하세요. 이렇게 하면 새 퓨즈 납땜이 훨씬 쉬워집니다.

4. **새 퓨즈 장착:** 새 퓨즈를 조심스럽게 위치시키고 제자리에 납땜합니다. 퓨즈를 고정하려고 눌러야 한다면, 으스러뜨리지 않도록 매우 부드럽게 누르세요.

**3단계: 재조립**

> [!WARNING]
> **중요한 재조립 단계:** 아래 단계 중 하나라도 빠뜨리면 장착 문제나 과열이 발생합니다.

1. **플라스틱 plate를 잊지 말기:** chip과 heat sink 사이에 들어가는 플라스틱 plate가 있습니다. 이것을 잊으면 heat sink가 올바르게 장착되지 않고 모든 것을 다시 분해해야 합니다.

2. **thermal paste 바르기:**
   - microfiber cloth와 rubbing alcohol로 기존 thermal paste를 닦아냅니다(**paper towel 금지!**).
   - 새 thermal paste를 바릅니다. 이 기기는 얻을 수 있는 모든 냉각 도움이 필요하므로, 너무 적게 바르는 것보다는 약간 더 많이 바르는 편이 낫습니다.

3. **RF shield를 조심해서 다루기:** GPS mount 아래의 RF shield(foil tape로 연결된 작은 금속 상자)는 까다로울 수 있습니다. 다시 제자리에 clip할 때 부드럽고 인내심 있게 다루세요. 일부 clip은 변형되어 있었다면 약간 다시 구부려야 할 수 있습니다.

4. **U.FL wire를 올바르게 배선하기:** 재조립할 때 다른 U.FL wire(heat sink에 장착된 PCB로 가는 선)를 heat sink 아래가 아니라 heat sink *주변*으로 지나가게 해야 합니다. 지나가야 할 위치에는 플라스틱 plate에 작은 notch가 있습니다. 아래로 지나가면 heat sink가 제대로 장착되지 않습니다.

5. **가운데 U.FL connector 연결:** 이 “다른 U.FL wire”는 heat sink 아래 보드의 가운데 U.FL connector에 연결됩니다. 올바른 connector를 가리키는 보드의 화살표 표시를 찾으세요.

**추가 사진**:

<img src="https://github.com/user-attachments/assets/ac314868-e601-4ce9-85e6-1e1000711b7f" width="500"/>
<img src="https://github.com/user-attachments/assets/86a5fea5-8cfe-4c71-87e2-1edee90d0fc8" width="500"/>
<img src="https://github.com/user-attachments/assets/96b5149a-a7b9-4eed-a89b-f5d98e95c76e" width="500"/>
<img src="https://github.com/user-attachments/assets/c0726345-812c-4585-89b4-aac84f3a9d93" width="500"/>
<img src="https://github.com/user-attachments/assets/c1daa5ed-2a0c-436c-98f7-3b52971bc947" width="500"/>

**자료**:

* USB-C/OBD-C 포트 수리 분해 part 1: https://www.youtube.com/live/TE757kH3EMM
* USB-C/OBD-C 포트 수리 분해 part 2: https://www.youtube.com/live/gTw_Qq8scqo

**예시**:

* [katsu의 C3 (OPC) ✅](https://discord.com/channels/771493367246094347/771493367779295304/1368055272488308797)
* [idnot의 C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1372254806449848412)
* [Le Potatos의 C3 (OPC) ✅](https://discord.com/channels/771493367246094347/771493367779295304/1374310506088628235) - 대안으로 shunt했습니다. 이 C3는 고장난 팬 같은 다른 문제도 있었을 수 있으며, 그 때문에 퓨즈 shunt가 필요했을 수 있습니다.
* [Nabeel의 C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1382502275460890755) - 고장난 OBD-C 케이블 때문에 발생했을 가능성도 있습니다.
  * 자세한 내용은 [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)를 보세요.
* [wferr의 C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1383249237739049080)
* [dazoe의 C3 ⚠️](https://discord.com/channels/469524606043160576/871838269405556736/1382566915465150464)
  * 참고: C3의 퓨즈는 전원이 꺼졌을 때는 정상으로 읽혔지만, 전원이 켜진 상태에서는 큰 저항을 보였습니다. 전원이 켜졌을 때만 voltage drop이 보였습니다.
  * ⚠️ dazoe의 C3 진단은 퓨즈 저항 측정보다 조금 더 복잡했고 더 고급 기술이 필요했습니다. 아래 내용이 불편하다면 더 지식이 많은 사람에게 도움을 요청하세요.
  * [“제 C3는 불안정하게 동작했습니다. 퓨즈(사진에서 OBD USB-C 바로 위)를 확인할 때, 퓨즈를 ‘warm up’한 뒤에야 0.8~1 ohm 값이 나왔습니다. 또한 보드가 동작하는 동안 퓨즈 양단의 voltage drop을 조심스럽게 측정했습니다. 완전히 부팅되지는 않고 ‘press any key to shutdown’이라고 적힌 화면에서 idle 상태로 있었습니다. voltage drop은 0.5에서 2.5v까지 들쭉날쭉했고, 이는 퓨즈의 저항이 변하고 있다는 뜻입니다.”](https://discord.com/channels/469524606043160576/871838269405556736/1383803066536431768)
  * [“heatsink 없이 전원을 켜 두는 것만으로도 과열 위험이 있습니다. 더 큰 위험은 전원이 들어간 상태에서 한 번 미끄러지면 심각한 손상을 줄 수 있다는 점입니다. probe를 넣기엔 공간이 좁고 USB port shield 바로 옆이라 power supply를 short시킬 위험이 있습니다. 추가한다면 굵고 크게 경고를 넣겠습니다. 기본 개념은 multimeter를 voltage mode로 두고 probe를 퓨즈 양쪽에 대는 것입니다. 전원이 들어왔을 때 voltage는 0에 가까운 상태를 유지해야 합니다.”](https://discord.com/channels/469524606043160576/871838269405556736/1383848416626479165)
* [dimdom69의 C3X (OPC) ✅](https://discord.com/channels/771493367246094347/834826173795139584/1388357047522689045)
  * “불량품에서는 2.0 ohm을 측정했고, 새 것은 0.0 ohm으로 측정했습니다.”
  * [고장난 OBD-C 케이블 때문에 발생했을 가능성도 있음?](#the-bad-obd-c-cable-case)
* [wabash의 C3, 다만 진단과 해결이 꽤 깔끔하지 않았음 ❓](https://discord.com/channels/469524606043160576/871838269405556736/1395147642581024789)
  * 측정에 퓨즈 제거가 필요 없다는 것을 모르고 측정 전 퓨즈를 제거하려다 실수로 녹였습니다.
  * 실제로 퓨즈가 나갔는지는 확실하지 않습니다.
  * 여전히 radar 문제가 있어 퓨즈가 유일한 문제였는지 명확하지 않습니다.
  * GPS 문제도 있습니다.
* [chaheeto의 C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1400252232544551085)
  * 퓨즈에서 1 ohm을 측정했고, 새 것으로 교체한 뒤 이제 작동합니다.
* [/u/AlekWishes의 C3X ✅](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comment/n56u9tn/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
  * “konik AI 교체용 SOM을 구매했고, 함께 제공된 파란 paste와 회색 paste를 사용했습니다. 원래 paste는 옆으로 발라져 있어 제대로 덮지 못했고, 특히 wifi RF cage에는 paste가 거의 없었습니다. 저는 3X를 가지고 있습니다. 말씀하신 것처럼 thermals는 괜찮고, 제대로 된 thermal paste 적용만 필요합니다. 처음 수리 시도 때 PMIC cap 하나가 short난 것을 발견했고, 교체하자 current draw가 없어졌습니다. PMIC 교체도 시도했지만 변화가 없어 포기하고 SOM 전체를 교체했습니다. 얼마 지나지 않아 이전의 과도한 current draw 때문에 USB port용 12v resettable fuse가 고장나고 있음을 발견했고, 그것을 교체한 뒤 몇 달 동안 모든 것이 아주 잘 작동하고 있습니다.”
  * [SOM 불량 또는 사망 사례](#the-bad-or-dead-som-case)와 관련 있습니다.
* [/u/Crabs2336의 C3X ✅](https://www.reddit.com/r/Comma_ai/comments/1mg0miu/comment/n7bqfrk/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
  * 퓨즈 교체 대신 shunt하는 쪽을 선택했습니다.
* [Catloaf의 C3 ❌](https://discord.com/channels/469524606043160576/871838269405556736/1403834860828622909)
  * 나간 퓨즈 3개를 교체했고, 기기는 wall 5V power에서는 잘 작동했습니다.
  * 차량에 꽂자 기기가 부팅을 시작했지만 곧 연기가 나고 차량 퓨즈 3개가 각각 나갔습니다.
  * 사고 이후 차량 시동이 걸리지 않게 되었습니다.
  * [차량은 퓨즈 교체로 수리되었습니다.](https://discord.com/channels/469524606043160576/525718620517564446/1403833844762677360)
  * 더 이상 C3를 사용하지 않습니다.
  * **경고**: 이 수리는 마음 약한 사람을 위한 것이 아닙니다. 경험 많은 사용자도 심각한 문제를 겪을 수 있습니다.
* [silverwing의 C3 🛑 (OPC)](https://discord.com/channels/771493367246094347/771501905507123200/1405664424693600346)
  * 퓨즈 위치를 찾는 데 매우 큰 어려움을 겪었습니다.
  * 전기 지식이 많지 않았습니다.
  * 퓨즈에서 “`0`” 저항을 측정했습니다. 솔직히 소수점 자릿수가 좀 부족해 보입니다.
  * 포기하고 comma에 “repair”를 보낼 예정입니다.
* [balsa의 C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1407407484980953321)
  * [처음에는 capacitor라고 생각했습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1402027821215387668)
  * [0.2 ohm, 0.8 ohm](https://discord.com/channels/469524606043160576/871838269405556736/1405600027644002407)
  * [flashing 중 몇 가지 문제가 있었습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1405659939602432170)
  * [solder blob으로 shunt했습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1405600064029720707)
  * “부품을 제거하고 bridge를 넣은 제 기기는 지금 꽤 잘 작동하고 있습니다.”
  * [팬 사망 사례](#the-fan-death-case)의 같은 C3입니다.
* [sidthebear의 C3 🛑](https://discord.com/channels/469524606043160576/871838269405556736/1407510430305357946)
  * “약 3년 후 제 c3가 boot looping을 시작했습니다. 아주 더울 때는 부팅해서 traffic screen까지 갔다가 즉시 reboot합니다. 그리고 계속 10~30분 정도 반복하다가 결국 켜진 상태를 유지합니다.”
  * 18.2 ohm을 측정했습니다.
  * 다시 조립하지 못했습니다.
  * [`#for-sale`에 $100로 올렸습니다.](https://discord.com/channels/469524606043160576/1407749221242900604/1407750793049800864)
  * 새 C3X로 교체했습니다.
  * [“trade-in이 아니라 private sale로 하는 건가요? 그냥 더 쉽습니다. 다시 조립하려고 애쓰고, 소프트웨어를 base op로 다시 올리고, 그 밖의 일을 처리하는 번거로움을 겪고 싶지 않았습니다. 특히 trade-in 기기로 받게 될 얼마 안 되는 할인 때문에 그러고 싶지는 않았습니다.”](https://discord.com/channels/469524606043160576/1407749221242900604/1407750473544499231)
* [rifker의 C3 (정말 이 사례였는지는 불명) ❓](https://discord.com/channels/469524606043160576/871838269405556736/1408153264641413245)
  * 1년 동안 서랍에 두었고, 다시 부팅되지 않았습니다.
  * comma의 repair service를 이용했고, Chase Sapphire Preferred의 Extended Warranty가 수리에 대한 warranty 처리를 승인했습니다.
  * 퓨즈를 측정하려 했지만 이미 나사 두 개가 stripped되어 있었습니다.
* [bscholer의 C3 (위 상세 지침) ✅](https://discord.com/channels/469524606043160576/871838269405556736/1408908722193039521)
  * 더운 차 안 앞유리에 일주일 동안 장착해 두었고, 그 뒤 더 이상 부팅되지 않았습니다.
    * *참고: 이후 한 번 boot logo가 약 0.5초 동안 잠깐 보였습니다. 그래도 작동하지는 않았습니다.*
  * 퓨즈에서 30 ohm을 측정했습니다.
  * 퓨즈 교체 후 C3가 완벽하게 작동합니다!
  * 여분 퓨즈를 샀으니, 미국에서 몇 개 필요하면 DM 주세요. 무료로 우편 발송해 드릴 수 있습니다.
  * [“네, 딱 그 퓨즈 하나였습니다. 다른 것들은 테스트하지 않았는데, 문제가 해결돼서 다행입니다 😅”](https://discord.com/channels/469524606043160576/871838269405556736/1410054918894784583)
  * 위 수리 가이드의 상당 부분을 기여했습니다!
* [posterduck의 C3 ❌](https://discord.com/channels/469524606043160576/871838269405556736/1410462125846958110)
  * bscholer의 가이드를 따라 진행했습니다.
  * “살아났습니다!”
  * [안타깝게도 밤사이 다시 퓨즈가 탄 것으로 보입니다.](https://discord.com/channels/469524606043160576/871838269405556736/1410972090341003274)
  * [“제 C3는 공식적으로 죽은 것 같습니다. 모든 퓨즈는 정상으로 나오지만, C3는 꽂아도 아무런 생명 징후가 없습니다 🙁”](https://discord.com/channels/469524606043160576/871838269405556736/1413005716146622617)
* [thinkpad4by3의 C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1411598315656839169)
  * “PTC fuse 4개를 모두 새 것으로 교체했지만 fault는 여전히 있습니다. c3가 전체 제어를 포기하고, 화면이 검게 되고, 알람이 울리고, ACC가 disengage됩니다. 이상한 점은 뽑았다가 다시 꽂으면 relay가 자동으로 열리지만 c3는 부팅하지 않는다는 것입니다. 이후 한동안 부팅하지 않습니다.”
  * [Mr One: “CPU에 문제가 있는 것 같습니다.”
](https://discord.com/channels/469524606043160576/871838269405556736/1411625935547007016)
  * [SOM 불량 또는 사망 사례](#the-bad-or-dead-som-case)
  * 수리 후 퓨즈 저항이 여전히 같은지 질문했습니다.
  * [이후에도 주변 온도 약 60F에서 frogpilot의 Always On Lateral을 사용해 계속 사용했지만, ACC는 사용하지 않았습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1412187801650331670)
  * [“결국 둘의 조합이었던 것 같습니다. 하지만 모든 퓨즈를 교체하고 OBD-C cable을 바꾼 뒤 지난 4~5주 동안 실패가 0번이었습니다.”](https://discord.com/channels/469524606043160576/871838269405556736/1418306528108089475)
  * 이 사례의 원인 중 하나로 [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)도 참고하세요.
* [xyrx의 C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1413628340681703455)
  * “엄지가 데이고 정말 형편없는 납땜을 2시간 한 끝에 작동시켰습니다.”
* [nisparks의 기기 ❌](https://discord.com/channels/469524606043160576/871838269405556736/1425561727746969730)
  * 위쪽 퓨즈에서 약 2.6+ ohm을 측정했습니다(다른 퓨즈는 0.6~1.0 ohm).
  * Digikey에서 V12(Bourns MF-NSML380/12-2) 퓨즈 10개를 배송 포함 약 $15.50에 주문했습니다.
  * [수리 후 이전보다 훨씬 더 많이 작동함](https://discord.com/channels/469524606043160576/871838269405556736/1430332221696380968)
  * [“이제 기기는 무작위 freeze, 매우 큰 alarm, 그리고 reboot 후 모든 것이 괜찮은 상태로 작동합니다. 때로는 40분, 때로는 더 오래 갑니다.”](https://discord.com/channels/469524606043160576/871838269405556736/1434652515730849883)
* [FrogsGoMoo의 C3 ✅](https://discord.com/channels/469524606043160576/871838269405556736/1434992550153814096)
  * 다른 shop들이 도움을 주지 못한 뒤 Drago가 수리했으며, 빠르고 효과적인 수리에 대해 매우 호평했습니다.
* [kyle의 C3X ✅](https://discord.com/channels/469524606043160576/871838269405556736/1440864351061020733)
  * Drago가 수리했습니다.
  * “traffic screen으로 loading할 때 black screen/turn off가 발생했습니다.”
  * 퓨즈가 교체되었고 이제 다시 작동합니다.
* [stwij의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1471948641920094218)
  * 퓨즈를 교체하고 SOM을 reflow했으며(Drago가 진행), 일시적으로 다시 살아났습니다.
  * 몇 번 주행한 뒤 다시 crash/reboot가 시작되었습니다.
  * 공식 수리를 위해 comma에 보낼 예정입니다.
  * [SOM 불량 또는 사망 사례](#the-bad-or-dead-som-case)도 참고하세요.

<a id="the-bad-supercapacitor-case"></a>
### 슈퍼커패시터 불량 사례

**증상**:

* 연결했을 때 기기 전원이 켜지지 않습니다.
* 기기가 켜진 상태를 유지하지 못합니다.
* [퓨즈가 나간 사례](#the-blown-fuse-case)와 비슷한 증상이지만, 퓨즈 테스트 결과는 양호합니다.
* 기기가 short circuit 또는 전원 문제의 징후를 보일 수 있습니다.

**진단**:

[퓨즈가 나간 사례](#the-blown-fuse-case)가 훨씬 더 흔하지만, comma three 계열 기기에서 supercapacitor 고장이 발생하는 드문 경우가 있습니다. comma 3와 comma 3X 모두 전원 구조의 일부로 supercapacitor를 사용합니다. 특히 comma 3X는 voltage stability를 위해 boost regulator와 함께 사용합니다.

> [!WARNING]
> 불량 supercapacitor를 의심하기 전에, [퓨즈가 나간 사례](#the-blown-fuse-case)의 지침에 따라 **항상 퓨즈를 먼저 확인하세요**. 퓨즈가 원인인 경우가 훨씬 더 흔하고, 진단과 교체도 더 쉽습니다.

> [!IMPORTANT]
> supercapacitor를 진단하고 교체하려면 다음을 포함한 전자 수리 기술과 장비가 필요합니다.
> - 더 큰 capacitor 부품을 식별하고 측정할 수 있는 능력
> - 적절한 tip이 있는 soldering iron
> - capacitance 측정 기능이 있는 multimeter
> - power circuit analysis에 대한 지식
>
> **퓨즈와 달리, supercapacitor는 정확한 테스트를 위해 보드에서 제거해야 하는 경우가 많습니다.** 따라서 in-circuit으로 할 수 있는 퓨즈 테스트보다 진단이 더 복잡합니다.
>
> 부품 수리 경험이 없다면 다음을 고려하세요.
> - 전문 전자 수리 서비스의 도움을 받기
> - comma의 out-of-warranty repair service 이용

**해결 방법**:

퓨즈가 양호하다는 것이 확인되었고 다른 원인을 배제했다면, 고장난 supercapacitor가 문제일 수 있습니다. 일반적으로 다음이 필요합니다.

1. **식별**: 육안 검사(부풀어 오름, 변색, 누액) 또는 전기적 테스트(short circuit, spec을 벗어난 capacitance)를 통해 고장난 supercapacitor를 찾습니다.
2. **교체**: 고장난 supercapacitor를 제거하고 적절한 교체 부품으로 바꿉니다.
   * 원래 부품: [Tecate Group, 2.7V, 1.5F, 파란 외장](https://www.tecategroup.com/products/data_sheet.php?i=TPLH-2R7/1.5WR6X15)
   * 대체품(더 높은 온도 rating): Knowles DGH155M2R7 (1.5F 2.7V), 자세한 내용은 아래 ereish64 사례를 보세요.
3. **검증**: short 또는 전원 문제가 해결되었는지 보드를 테스트합니다.

supercapacitor는 일반적인 surface-mount capacitor보다 큰 부품이라 진단과 교체를 위해 접근하기가 더 쉬울 수 있습니다.

**예시**:

* [ereish64의 C3X](https://github.com/ophwug/docs/issues/25) ✅
  * 전원 문제와 일치하는 증상을 보고했습니다.
  * 조사 결과 supercapacitor 관련 문제(1.5F capacitor)가 의심되었습니다.
  * supercapacitor를 성공적으로 교체했고 기기가 작동합니다.
  * 대체 교체 부품: [Mouser](https://www.mouser.com/ProductDetail/Knowles-Illinois-Capacitor/DGH155M2R7?qs=iLbezkQI%252BshcZvBCu9GXdg%3D%3D)의 Knowles DGH155M2R7 (1.5F 2.7V)
    * 참고: 교체 부품은 원래 footprint에 정확히 맞지는 않지만, 조심스럽게 설치하면 사용할 수 있습니다.
    * 교체 부품은 더 높은 온도 rating을 가집니다(85C vs 원래 65C). “제가 교체품으로 사용한 capacitor는 최대 온도가 +85C입니다. 원래 capacitor는 최대 +65C로 보입니다...”
  * 자세한 논의와 사진은 [issue](https://github.com/ophwug/docs/issues/25)를 보세요.

**판매처**:

* comma OEM: TPLH-2R7/1.5WR6X15
  * Datasheet: https://www.tecategroup.com/products/data_sheet.php?i=TPLH-2R7/1.5WR6X15
  * Digikey: https://www.digikey.com/en/products/detail/tecate-group/TPLH-2R7-1-5WR6X15/9930255
* ereish64의 더 높은 온도 rating 대체품: DGH155M2R7
  * https://www.mouser.com/ProductDetail/Knowles-Illinois-Capacitor/DGH155M2R7?qs=iLbezkQI%252BshcZvBCu9GXdg%3D%3D
  * [issue](https://github.com/ophwug/docs/issues/25)에 있는 그의 이미지를 참고하세요.

<a id="the-bad-emi-filters-case"></a>
<a id="the-bad-screen-emi-case"></a>
<a id="the-screen-doesnt-work-or-is-dying-case"></a>
### 화면이 작동하지 않거나 죽어 가는 사례

**증상**:

* `openpilot`은 여전히 engage됩니다.
* speaker에서 소리가 여전히 들립니다.
* fan이 움직이거나 소리가 들립니다.
* 기기의 LED가 깜빡입니다(예: 부팅 시 빨간색 후 파란색).
* 화면이 켜지지 않습니다.
* 화면에 보라색 얼룩이 있습니다.
* Screen burn-in
* 기기가 home network에 여전히 나타납니다.
* Linux OS AGNOS가 부팅되어 작동 중임을 보여 주는 다른 모든 징후
* 전원 문제가 아닌 경우([퓨즈가 나간 사례](#the-blown-fuse-case) 참고)

**증상이 아닌 것**:

* Screen tearing - [이는 특정 기간 동안 openpilot과 openpilot fork에 영향을 준/주고 있는 소프트웨어 문제였습니다.](https://github.com/commaai/openpilot/issues?q=is%3Aissue%20state%3Aopen%20tearing) 최신 comma openpilot 또는 openpilot fork로 업데이트하세요.

![이미지](https://github.com/user-attachments/assets/91e0bcc8-f625-4640-8aeb-2a227f18d523)

**해결 방법**:

먼저 화면 연결을 다시 끼워 보세요. 그래도 작동하지 않으면 화면을 교체해야 합니다.

> [!WARNING]
> **화면 ribbon을 다시 연결할 때 조심하세요.** 그 옆의 두 IC는 매우 약합니다. connector를 끼우려다 미끄러지면 그 IC 중 하나에 걸려 깨질 수 있고, 결국 화면이 pixelated mess가 되거나 아예 아무 그림도 나오지 않을 수 있습니다.
>
> 검은 화면은 보통 [퓨즈가 나간 사례](#the-blown-fuse-case) 또는 [SOM 불량 또는 사망 사례](#the-bad-or-dead-som-case)를 의미할 수 있습니다. 하지만 뒷면을 열고 기기를 꽂았을 때 fan이 돌기 시작하고 panda light가 깜빡인다면, 퓨즈와 SOM은 괜찮을 수도 있습니다. 그럴 때는 screen connector 옆 IC를 close-up으로 촬영해, 깨져 나간 부분이 없는지 확인해야 합니다. 이 부품들은 유리처럼 깨집니다. 이는 [Bad EMI Filters Case](#the-bad-emi-filters-case) 또는 [Bad Screen EMI Case](#the-bad-screen-emi-case)를 나타낼 수 있습니다.

주변 MOSFET에 고장 징후가 있는지 검사하세요. [MOSFET이 탄 사례](#the-burned-mosfet-case)를 참고하세요.

Konik.ai에는 C3X와 비슷할 것으로 보이는 자사 기기용 화면 교체 가이드가 있습니다: https://www.youtube.com/watch?v=ieyz4pxaHxU

큰 흐름의 지침은 C3/C3X뿐 아니라 어떤 기기에서도 여전히 같습니다. 모든 나사를 풀고 케이블을 손상시키지 않도록 조심하는 것입니다.

* 공식 comma.ai 화면으로 교체한다면, QR code sticker 사진을 찍어 보관하세요. 그 안에 color calibration data가 들어 있습니다.
* Comma.ai는 C3용 replacement screen을 _case 포함_ 으로 판매하지 않습니다. bare screen을 comma 또는 타사에서 구매하고, 모바일 수리점에 기존 화면 교체를 맡기세요.
* “front case” 옵션이 포함된 교체품은 glue-less repair experience라 모바일 수리점 도움이나 비슷한 경험이 필요하지 않습니다.
* “front case”가 없으면 “B7000 glue로 frame에 붙일 수 있습니다”(Konik.ai 인용).
* [화면 색상이 매우 이상한 사례](#the-screen-colors-are-really-off-case)도 확인해 보고 싶을 수 있습니다.

**판매처**:

* comma.ai: https://comma.ai/shop/comma-device-screen
  * C3X용은 front case 포함으로 판매합니다. C3 front case 포함 제품은 오래전부터 품절입니다.
* Mr. One: https://oneclone.net/product/kidney-beans-organic/
* Konik.ai: https://konik.ai/shop/a1-amoled-screen/
* Amazon: https://amzn.to/3KvnDRe
* “Huawei Mate 10 Pro”용 panel이라면 어떤 것이든 찾아서 사용할 수 있습니다. 품질은 다를 수 있습니다. 모든 screen이 작동하는 것은 아닙니다. 작동한다고 알려진 것은 AMOLED version입니다. TFT와 저가 모델은 작동하지 않을 수 있습니다.
  * 사용하지 않는 camera cutout은 nail polish로 메울 수 있습니다 💅.

**예시**:

* [radko의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1407751155680804914)
  * “화면 교체는 아주 쉬웠습니다. sticky tape를 쉽게 제거할 수 있게 만들고 ribbon cable을 어디서 구부려야 하는지 표시해 둔 HW team에게 잘했다고 말하고 싶습니다 🥰”
  * “2022년 11월에 산 c3입니다. 사용자 실수로 화면이 죽었습니다(dashboard 아래로 미끄러져 차량 infotainment screen에 부딪힘). 며칠 뒤 화면이 완전히 죽었습니다. 부딪히기 전에는 완벽하게 작동했습니다.”
  * [“DIY입니다. hair dryer로 2분 동안 천천히 데우니 glue가 원래 화면을 꽤 쉽게 놓아주었습니다. 원래 glue가 아직 끈적해서 재사용했습니다. 깨진 화면을 살펴봤지만 crack은 찾지 못했고, 아마 *정확한* 지점을 맞아 뒤쪽 OLED의 organic matter가 빠져나온 것 같습니다. 흥미롭게도 touch panel에도 ghost touch가 있었지만 부팅 시 reset을 일으킬 정도로 자주 발생하지는 않았습니다(12V 절약을 위해 OBD를 분리한 상태로 실행). 위 사진에서는 위치를 다시 잡다가 calibration reset에 성공했습니다.”](https://discord.com/channels/469524606043160576/871838269405556736/1407944207108145245)
* [chichum의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1438958679968972851)
  * 기기가 약 5일 동안 unplugged 상태였고 다시 켜지지 않았습니다.
  * 꽂으면 장치가 빨간색으로 빠르게 깜빡인 뒤 파란색으로 깜빡였습니다. 화면은 전혀 켜지지 않았지만 fan은 움직였습니다.
  * 여러 cable과 plug를 시도한 뒤, 사용자는 blown fuse를 의심하고 교체품을 주문했습니다.
  * 최종 문제는 bad screen이었습니다. 사용자가 이를 판단한 이유는 기기를 차량에 꽂고 steering wheel로 openpilot을 활성화했을 때 차량이 스스로 주행하기 시작했기 때문입니다. 이는 display를 제외하면 기기가 완전히 정상 작동 중임을 나타냅니다.
  * 이 사례는 blown fuse 같은 전원 문제를 가정하기 전에 생명 징후(깜빡이는 불빛, fan 소리, openpilot engagement)를 확인하는 것이 중요함을 보여 줍니다.
  * 화면은 첫날 떨어뜨려 금이 갔고, 이것이 몇 년 뒤 고장에 영향을 주었을 수 있습니다.
  * 화면은 교체하지 않을 예정이며, 아마 comma four로 trade-in할 것입니다.
* [Drago 고객의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1458989097472495768)
  * 화면은 양호했지만...
  * 참고: 이 사례는 알려진 정상 화면에서 dead touch 문제를 일으킨 bad SOM 사례였습니다.
  * 자세한 내용은 [SOM 불량 또는 사망 사례](#the-bad-or-dead-som-case)를 보세요.

<a id="the-fan-death-case"></a>
### 팬 사망 사례

**증상**:

* 기기가 과열됩니다.
* 팬에서 끔찍한 소리가 납니다.
* 팬이 돌지 않습니다.

한국식 “fan death”가 아닙니다!

**해결 방법**:

안타깝게도 comma는 replacement fan만 따로 판매하지 않습니다. 사용자들은 다양한 fan으로 교체해 왔고, 성공 정도는 제각각입니다. [comma는 OEM 부품이 ADDA 제품일 수 있지만 기성품인지는 확실하지 않다고 말했습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1374440250486554644) Mr. One은 C3용 heatsink 포함 replacement fan을 판매합니다.

함께 보기: [청소되지 않은 팬 플럭스 사례](#the-uncleaned-fan-flux-case)

**예시**:

* [redmapleleaf의 C3, Noctua](https://discord.com/channels/469524606043160576/871838269405556736/1328667993047040010)
* [Pandus의 C3, ZOTAC fan 재활용](https://discord.com/channels/469524606043160576/871838269405556736/1364305247723589734)
* [Balsa의 C3, Mr. One의 C3 Fan Replacement Heatsink](https://discord.com/channels/469524606043160576/871838269405556736/1415378929899798569)
  * replacement fan 사진이 있지만, standalone non-square shroud 버전은 찾을 수 없는 것으로 보입니다.
  * [fan testing script도 실행했습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1415385666597945517)
  * [퓨즈가 나간 사례](#the-blown-fuse-case)의 같은 Balsa입니다.

**판매처**:

* Mr. One: https://oneclone.net/product/c3-heatsink-replacement-parts/
  * C3용 heatsink 포함 replacement fan
  * Mr. One에는 C3X의 “clone”인 C3XL이 있지만, 물리적으로는 여전히 C3와 비슷하며 comma C3X와 호환되지 않습니다.

**참고**:

* Fan Test: https://www.youtube.com/watch?v=4BmkMEpBcLY
* https://discord.com/channels/469524606043160576/871838269405556736/1350189845758218417
* comma: https://discord.com/channels/469524606043160576/871838269405556736/1374440250486554644

<a id="the-uncleaned-fan-flux-case"></a>
### 청소되지 않은 팬 플럭스 사례

**증상**:

* fan을 고정 level로 설정해도 fan speed가 일정하지 않습니다.
* panda script에서 fan RPM reading이 0입니다.
* fan의 파란색 speed control wire를 분리해도 maximum speed로 돌지 않고 계속 oscillate합니다.

> “comma three rev I의 fan pin에 flux가 청소되지 않음 - 08/31/21”

<img width="640" height="360" alt="flux" src="https://github.com/user-attachments/assets/578d4338-2139-426d-b793-740d4f451051" />

**해결 방법**:

fan pin에서 flux를 청소하면 fan이 올바르게 동작해야 합니다.

함께 보기: [팬 사망 사례](#the-fan-death-case)

**예시**:

* [alesatobrazilsp 친구의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1408258565726015590 )
  * [원래 issue post](https://discord.com/channels/469524606043160576/871838269405556736/1397284881054306364)

<a id="the-poor-gps-signal-case"></a>
### GPS 신호 불량 사례

**증상**:

* 기기에 poor GPS signal alert가 있습니다.
* 기기가 [comma connect]에서 자기 위치를 잘 찾지 못하는 것처럼 보입니다.
* 환경 조건:
  * 자석식 mount가 사용됩니다.

   * 차량 windshield가 heated windshield입니다.

**해결 방법**:

이 문제에는 여러 해결책이 있습니다.

* 최신 openpilot은 GPS가 alert를 띄워야 하는 필수 조건인지 신경 쓰지 않습니다. https://github.com/commaai/openpilot/pull/35585
  * 이 변경이 포함된 codebase로 업데이트하세요.
  * 그래도 [comma connect]에 기록되는 map behavior는 이상할 수 있지만, 지속적인 alert는 발생하지 않습니다.
* 하드웨어 문제:
  * 내부 GPS antenna 연결을 확인하세요.
  * GPS module에 전원 연결이 되어 있는지 확인하세요.
* Heated windshield는 GPS 수신에 문제를 일으킬 수 있습니다.
  * 아직 탐구되지는 않았지만, 이를 돕기 위해 사용할 수 있는 GPS repeater가 있습니다. 성공했다면 알려 주세요.

**예시**:

* [Nabeel의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1383159801365790932)
  * “수리 후 제 C3에서 GPS가 왜 작동하지 않았는지 발견했습니다… 이것이… 제 책상 위에 놓여 있었습니다... GPS module을 main board에 연결하는 cable입니다.”

<a id="the-bad-or-dead-som-case"></a>
### SOM 불량 또는 사망 사례

System-On-Module(SOM)은 comma 기기의 주 처리 장치로, CPU, memory 및 기타 핵심 computing component를 포함합니다. SOM이 고장나거나 손상되면 기기는 작동하지 않습니다.

> [!WARNING]
> 이 섹션은 WIP이며 작성 중입니다.

**증상**:

* 기기가 부팅되지 않습니다.
* 기기 전원이 켜지지 않습니다.
* 퓨즈가 양호합니다. 자세한 내용은 [퓨즈가 나간 사례](#the-blown-fuse-case)를 보세요.
* serial에서 기기가 TODO: bad boot message 예시로 채우기
* touch screen 문제(dead touch).
  * 정상인 SOM으로 교체했을 때 문제가 해결되면 확인할 수 있습니다.
* 알려진 정상 SOM(아마 빌린 것)으로 교체하면 문제가 해결됩니다.

**해결 방법**:

> [!NOTE]
> 기존 SOM에서 key를 추출하는 방법에 대한 지침으로 채우기. https://discord.com/channels/469524606043160576/1346999805624320084/1355086750724128929

* **SOM reflow**: 특히 touch issue의 경우 문제를 일시적 또는 영구적으로 고칠 수 있습니다. 매우 어렵기 때문에 전문가 도움을 받거나 SOM을 아예 교체하는 쪽을 선호해야 합니다. Vendor 섹션을 확인하세요.
* **SOM 교체**: System-On-Module(SOM)을 새 것으로 교체합니다. 그런 다음 flash합니다.

**예시**:

* [/u/AlekWishes](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comment/n56u9tn/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
  * “konik AI 교체용 SOM을 구매했고, 함께 제공된 파란 paste와 회색 paste를 사용했습니다. 원래 paste는 옆으로 발라져 있어 제대로 덮지 못했고, 특히 wifi RF cage에는 paste가 거의 없었습니다. 저는 3X를 가지고 있습니다. thermal paste 적용 QC가 좋지 않아 비슷한 과열 문제를 보는 사람이 더 많아도 놀랍지 않을 것 같습니다. 말씀하신 것처럼 thermals는 괜찮고, 제대로 된 thermal paste 적용만 필요합니다. 처음 수리 시도 때 PMIC cap 하나가 short난 것을 발견했고, 교체하자 current draw가 없어졌습니다. PMIC 교체도 시도했지만 변화가 없어 포기하고 SOM 전체를 교체했습니다. 얼마 지나지 않아 이전의 과도한 current draw 때문에 USB port용 12v resettable fuse가 고장나고 있음을 발견했고, 그것을 교체한 뒤 몇 달 동안 모든 것이 아주 잘 작동하고 있습니다.”
  * [퓨즈가 나간 사례](#the-blown-fuse-case)와 관련 있습니다.
* [Drago 고객의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1458989097472495768)
  * “failing SOM이 이전에도 touch issue를 일으킨 적 있나요?”
  * SOM 교체로 확인했습니다.
  * “reflow 후 touch가 다시 작동합니다.”
  * LightningHard SOM (C3X).
* [Fortissimo/ez2hero의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1469584236620021803)
  * “WIP”
  * [자신의 것을 reflow했습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1470737484370415636)
* [stwij의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1471948641920094218)
  * 퓨즈를 교체하고 SOM을 reflow했으며(Drago가 진행), 일시적 fix 역할을 했습니다.
  * 문제가 다시 돌아왔습니다(5V에서 freezing, 12V에서 rebooting).
  * 공식 repair/replacement를 위해 comma에 보낼 예정입니다.
  * [퓨즈가 나간 사례](#the-blown-fuse-case)도 참고하세요.

**판매처**:

SOM reflow:

* [Discord의 awuf/Drago - 이 작업에 관심이 있을 수 있습니다.](https://discord.com/channels/469524606043160576/871838269405556736/1459001876744765633)

교체용 SOM:

* comma.ai: SOM을 판매하지 않습니다.
* Mr. One: https://oneclone.net/product/thundercomm-d845-som-4gb64/
* konik.ai: https://konik.ai/shop/thundercomm-d845-som-4gb64/
  * 8GB version 옵션이 있지만 openpilot에는 필요하지 않습니다.

<a id="the-damaged-ribbon-cable-case"></a>
### 리본 케이블 손상 사례

**증상**:

* “long story short, 제 작은 뇌가 ssd를 넣으려고 너무 긴 나사를 썼고, crunching sound가 들렸고, 제가 본 것은 이렇습니다.”
* small brain

![IMG_1289](https://github.com/user-attachments/assets/ad788299-3c63-427d-b260-f4b5126e6e23)

**해결 방법**:

손상된 ribbon cable을 교체하세요.

**판매처**:

* [DigiKey](https://www.digikey.com/)

**예시**:

* [xyrx의 C3](https://discord.com/channels/469524606043160576/954493346250887168/1406453677891387454)
  * [DigiKey에서 맞거나 매우 비슷한 ribbon을 찾은 후속 내용](https://discord.com/channels/469524606043160576/871838269405556736/1409000268837683282 )
  * “핀 수를 세고 길이를 재기만 하면 됐습니다.”
  * https://www.digikey.com/en/products/detail/molex/0151660271/3281152 를 찾았습니다.
  * 이런 직선 케이블은 아마 찾기 쉬웠을 것입니다.

<a id="the-sim-card-is-stuck-case"></a>
### SIM 카드가 끼인 사례

comma 쪽 설계 결함에 약간 해당할 수도 있습니다. comma three 계열 기기의 플라스틱은 작은 SIM card를 눌렀다가 쉽게 제거하는 데 필요한, 가장 좋거나 정확한 opening을 항상 갖고 있지는 않습니다.

**증상**:

* SIM card를 눌렀는데 기기 안에 끼어 있습니다.

**해결 방법**:

* plier를 사용해 card를 꺼냅니다.
* 더 심각한 경우에는 screwdriver로 기기를 분해해 더 많은 접근 공간을 확보합니다.

**예시**:

* [Vrabetz의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1416214544304443473)
* [h3lix213412의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1416073425675358279)
  * “sim slot이 stuck되어 있어서, sim을 조금 힘줘 제거할 수 있는 지점까지 가려고 나사 두 개를 풀어야 했습니다.”
* [cookiemonster의 C3X](https://discord.com/channels/469524606043160576/524592892627517450/1414868691643924512)
  * “분해해 보니 sim card tray가 완전히 seated되는 지점에 가까워질수록 꽤 빡빡해지고 저항이 커졌습니다. 완전히 seated되면 spring이 겨우 밀어낼 정도입니다. 당분간 sim card를 바꿀 필요가 없기를 바랍니다 🫠”

<a id="the-stuck-on-registration-case"></a>
### 등록에서 멈춘 사례

C3 registration을 위한 comma endpoint가 약간 불안정할 수 있다고 의심됩니다. 최신 C3와 C3X에는 dongle id가 미리 loaded되어 있지만, 더 오래된 초기 C3에는 없을 수 있습니다. 어떤 기기는 다른 이유로 /persist에 dongle id가 없을 수도 있습니다.

**증상**:

* Registration이 계속 spinning 상태로 멈춰 있습니다.

**해결 방법**:

C3X를 사용 중이라면 최신 comma openpilot 또는 openpilot fork로 업데이트해 보세요. 최신 버전은 일부 registration 문제를 고쳤습니다.

그렇지 않다면 더 외과적인, 하지만 [comma가 권장하지 않는 해결책](https://discord.com/channels/469524606043160576/819046761287909446/1335013586027942065)이 있습니다.

https://connect.comma.ai 또는 https://useradmin.comma.ai 에서 자신의 dongle id를 찾습니다.

아래에서 dongle id를 교체한 뒤 이 script를 실행합니다.

```bash
DONGLE_ID="REPLACE_THIS_WITH_YOUR_DONGLE_ID"
sudo mount -o remount,rw /persist
echo "$DONGLE_ID" > /persist/comma/dongle_id
sudo mount -o remount,ro /persist
sudo reboot
```

<a id="the-bad-screen-connector-emi-filters-case"></a>
### 화면 커넥터 EMI 필터 불량 사례

![EMI Filter](https://github.com/user-attachments/assets/a6f31f61-0725-4b43-a9ea-613c55c6a797)

**증상**:

* 화면은 켜지지 않지만, 기기는 그 외에는 부팅됩니다(fan 회전, LED 점등, openpilot engage 등).
* 정상으로 알려진 replacement screen으로도 문제가 해결되지 않습니다.
* screen connector EMI filter(부품 `PCMF3USB3S`)가 불량입니다.
* screen ribbon connector 옆 EMI filter/chip이 탔거나, 깨졌거나, 그 밖의 손상된 모습입니다.

> [!NOTE]
> 이는 화면 connector 주변부가 손상된 증상일 수 있으며, 때로는 screen ribbon cable을 다시 연결하다가 미끄러져 발생합니다. 진단에 대한 자세한 내용은 [화면이 작동하지 않거나 죽어 가는 사례](#the-screen-doesnt-work-or-is-dying-case)의 경고를 보세요.

**해결 방법**:

이는 고급 micro-soldering 기술과 장비가 필요한 극도로 어려운 수리입니다.

* **필요한 도구**: Hot air rework station, solder wick, flux, microscope 또는 고배율 lens, 매우 안정적인 손, 그리고 많은 인내심.

해결 방법은 screen connector 옆의 손상된 EMI filter(`PCMF3USB3S`)를 교체하는 것입니다.

**판매처**:

* `PCMF3USB3S` filter는 대부분의 주요 전자 부품 웹사이트(예: Digi-Key, Mouser 등)에서 찾을 수 있습니다.

**예시**:

* [Drago 고객의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1439435620304031764)
  * [어려운 교체 과정의 예시](https://discord.com/channels/469524606043160576/871838269405556736/1439063062744404110)
  * [Drago의 또 다른 예시](https://discord.com/channels/469524606043160576/871838269405556736/1439080929548177490)
  * Drago는 수리 서비스를 제공할 수 있는 커뮤니티 멤버입니다. 직접 수리하는 것이 불편하다면 시도를 위해 연락해 보세요.

<a id="comma-three-c3"></a>
## comma three (C3)

출시: 2021-07-31

단종: 2023-10-12

Codename: tici

comma openpilot 개발/지원 중단: 2025-08-26, [Discord Announcement](https://discord.com/channels/469524606043160576/954493346250887168/1410079554529398947), [일부 커뮤니티 Reddit 논의](https://www.reddit.com/r/Comma_ai/comments/1n14uv8/the_c3_will_become_unsupported_starting_with_the/), `master`에서는 즉시 완전히 개발/지원 중단, 다가오는 `0.10.1` release에서도 중단

https://blog.comma.ai/comma-three-press-release/

comma three는 hacked-up cell phone 기반이 아닌, comma가 처음부터 설계한 첫 기기입니다.
가격은 비교적 비쌌습니다. 세 개의 카메라가 들어간 첫 기기였습니다.

comma three의 변형에는 SSD 없이 32GB onboard eMMC System on Module storage만 있는 버전, 256GB NVME SSD storage 버전, 1TB NVME SSD storage 버전이 포함될 수 있습니다.

지원되는 유일한 OEM SSD는 [Samsung 980 Non-Pro SSD](https://www.amazon.com/Technology-Intelligent-Turbowrite-MZ-V8V1T0B-AM/dp/B08V83JZH4?th=1)입니다. 다른 SSD는 작동하지 않거나 지원되지 않는 이상한 문제가 있을 수 있습니다. embedded device는 desktop이나 laptop보다 SSD에 훨씬 더 까다롭습니다.

**변화 과정**:

* 초기 C3에는 전용 u-blox GPS module이 있었습니다.
* SSD 없이 32GB onboard eMMC storage를 가진 버전이 나중에 도입되었습니다.
* [Panda]가 내부 USB 연결에서 SPI 연결로 변경되었습니다.
* C3 생애 주기 말기에 camera가 AR0231에서 OS04C10으로 변경되었습니다.


이런 변경의 날짜와 시간은 잘 문서화되어 있지 않지만, 존재한다는 것은 알려져 있습니다.

**자료**:

* https://enjoi.dev/posts/2021-12-20-comma-3-teardown/ - comma three에 대한 좋은 일반 written teardown.
* https://www.youtube.com/watch?v=Y3Z4j466CsE - SSD 설치
* USB-C/OBD-C 포트 수리 분해 part 1: https://www.youtube.com/live/TE757kH3EMM
* USB-C/OBD-C 포트 수리 분해 part 2: https://www.youtube.com/live/gTw_Qq8scqo

<a id="the-swampy-no-panda-case"></a>
### 축축했던 No Panda 사례

**증상**:

* [Panda] 없음

기기가 매우 습한 환경에 있었고 Panda의 MCU에 corrosion이 생겼습니다.

![이미지](https://github.com/user-attachments/assets/41717469-bcf0-4eec-88c1-a0da962cc76f)

**해결 방법**:

보드를 청소하고 corrosion을 제거하세요.

**예시**:

* [sparra215의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1359585271041233077)

<a id="the-screen-colors-are-really-off-case"></a>
### 화면 색상이 매우 이상한 사례

**증상**:

* 화면이 factory 상태에서 교체되었습니다.
* 색상이 이상합니다. 너무 파랗습니다.

**해결 방법**:

이 thread를 확인하세요: https://discord.com/channels/469524606043160576/1354453342000255199

C3에 설치해 색상을 고칠 수 있는 `color_cal` 파일이 여러 개 있습니다. 공식 comma.ai screen replacement가 없다면 몇 가지 다른 파일을 시도해 보는 것만으로도 성공할 수 있습니다.

<a id="the-burned-mosfet-case"></a>
### MOSFET이 탄 사례

**증상**:

* 화면 교체 후 화면 전원이 켜지지 않습니다.
* 보드에서 탄 MOSFET이 보입니다.

<img width="403" alt="Image" src="https://github.com/user-attachments/assets/d2b22aaa-6be4-45a0-900d-fe59ba6cb919" />

**해결 방법**:

탄 MOSFET을 새 것으로 교체합니다.

**예시**:

* [Ale Sato의 브라질 지인 C3](https://discord.com/channels/469524606043160576/871838269405556736/1359678982207045672)

<a id="the-camera-malfunction-case-c3"></a>
### 카메라 오작동 사례 (C3)

**증상**:

* 특정 camera가 언급된 Camera Malfunction message가 나타납니다.

**해결 방법**:

오작동하는 camera를 새 것으로 교체하세요. 다른 camera의 type과 맞는지 확인하세요. 예: OS04C10 또는 AR0231. 고장난 C3를 찾아 camera를 salvaging할 수 있을지도 모릅니다. 특정 type을 찾을 수 없다면, 모든 camera를 같은 type으로 교체해야 할 수 있습니다.

일부 vendor는 C3용 replacement camera를 판매합니다. 자신의 C3에 맞는 type의 camera를 구매해야 합니다. 한 가지 type의 camera만 보유하고 있을 수 있으므로, 모든 camera를 같은 type으로 교체해야 할 수 있습니다.

참고: C3X에서는 camera가 main board에 납땜되어 있으므로 이 작업이 불가능하거나 매우 어렵습니다. 그래서 이 사례는 C3 섹션에만 있습니다.

**예시**:

* [sparra의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1359555578606780608)

**판매처**:

* Mr. One: https://oneclone.net/product/c3-cameras/
* Konik.ai: https://konik.ai/shop/c3-cameras/

두 vendor 모두 OX03C10 variant만 판매한다는 점에 유의하세요.

<a id="the-nvme-drive-not-mounted-case"></a>
### NVMe 드라이브가 마운트되지 않는 사례

**증상**:

* NVMe drive가 mounted되지 않았다는 빨간 error message가 표시됩니다.

![이미지](https://github.com/user-attachments/assets/17e62a61-4591-499c-9084-87fe75720980)

**해결 방법**:

NVMe drive를 다시 장착하고, 적절한 electronic contact cleaning solution으로 connector를 청소하세요.

**예시**:

* [mikejake의 C3](https://discord.com/channels/469524606043160576/871838269405556736/1194379197712441364)

**자료**:

* https://www.youtube.com/watch?v=Y3Z4j466CsE - SSD 설치


<a id="comma-threex-c3x"></a>
## comma threex (C3X)

출시: 2023-10-12

단종: 2025-11-08, 다만 약 한 달 전부터 품절되기 시작했습니다.

Codename: tizi

https://blog.comma.ai/comma3X/

comma 3X는 comma three의 첫 주요 하드웨어 revision입니다. 큰 비용 절감을 거쳤고, 이제 제조 비용이 더 저렴합니다.

* camera는 더 이상 별도 board에 있지 않고 main board에 납땜되어 있습니다.
* NVMe SSD는 제거되었고, 대신 128GB onboard eMMC storage를 사용합니다.
* speaker가 두 개의 speaker로 전면 개편되었습니다.
* 훨씬 가볍습니다.
* comma three mount보다 작은 mount를 사용합니다.
* 이제 기기에 Red Panda가 포함되며, 내장 CAN-FD 지원이 포함됩니다.
* camera가 OX03C10으로 변경되었습니다.
* 전원 구조는 더 안정적인 전압과 신뢰성을 위해 supercapacitor와 boost regulator를 함께 사용하는 방식으로 업그레이드되었습니다.

**변화 과정**:

* Real-Time-Clock이 제거되었고 실장되지 않으며, 부팅 직후 GPS로 채워집니다.
* comma는 [기성 Thundercomm D845 SOM](https://www.thundercomm.com/product/d845-som/)에서 [자체 custom LightningHard SOM](https://blog.comma.ai/096release/#agnos-9)으로 전환했습니다([FCC ID](https://fcc.report/FCC-ID/2BFC6-LIGHTNINGH)).
  * [thermal을 더 잘 처리하도록 PMIC 수정](https://www.reddit.com/r/Comma_ai/comments/1m93ddx/comment/n56rj4i/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)
* [“No chiplet” Red Panda](https://discord.com/channels/469524606043160576/871838269405556736/1374440250486554644)
* ~ 2025년 4월: [고온에서 시작하려면 더 많은 command가 필요한 다른 panel](https://github.com/commaai/openpilot/issues/34971#issuecomment-2778764248)


<a id="the-no-panda-on-c3x-case-software"></a>
### C3X의 No Panda 사례 (소프트웨어)

**증상**:

* [Panda] 없음

**해결 방법**:

https://github.com/commaai/openpilot/issues/33016 절차를 진행하세요.

참고: openpilot의 `nightly` branch를 사용하세요. `master-ci`는 더 이상 사용할 수 없습니다.

**예시**:

* [Ed Moore의 C3X](https://discord.com/channels/469524606043160576/1263672324973138033/1270345888950124671)

<a id="the-no-panda-on-c3x-case-hardware"></a>
### C3X의 No Panda 사례 (하드웨어)

**증상**:

* [Panda] 없음
* https://github.com/commaai/openpilot/issues/33016 의 software solution을 10번 이상 시도해도 작동하지 않았습니다.

**해결 방법**:

comma openpilot이 설치되어 있어야 합니다.

SOM을 제거했다가 다시 장착하세요.

reboot하고 기다리세요.

SOM이 제대로 seated되지 않았을 가능성이 있었을까요?

**예시**:

* [ceem0money의 C3X](https://discord.com/channels/469524606043160576/1263672324973138033/1370771997188952116)

<a id="the-fried-panda-case-c3x"></a>
### C3X의 Panda가 타 버린 사례

**증상**:

* [Panda] 없음
* SOM을 다시 장착해도([C3X의 No Panda 사례 (하드웨어)](#the-no-panda-on-c3x-case-hardware) 참고) 문제가 해결되지 않습니다.

**원인**:

comma staffer Adeeb이 [Discord에서 설명했습니다](https://discord.com/channels/469524606043160576/1436852432503046294/1448044893304782879):

> OBD C를 통해서는 아닙니다. 기기를 열면 serial과 여러 다른 것들이 노출된 debug connector가 있습니다.
> 불량 USB cable이 VIN을 data line에 short시켜 3X의 panda가 타고 있었기 때문에 제거했습니다.

일부 C3X 기기에서는 내부 debug connector 구성 때문에 Panda chip이 불량 USB/OBD-C 케이블에 취약했습니다. 구체적으로, 불량 케이블이 VIN(12V)을 data line에 short시키면 높은 전압이 Panda를 태울 수 있습니다.

**해결 방법**:

* 복구 방법은 없습니다. Panda가 타 버린 것입니다.
* 기기, panda chip 및/또는 board를 교체해야 할 가능성이 큽니다.

**예시**:

* 이 문제는 아직 널리 공개된 예시는 없지만, comma staff가 확인했습니다.

<a id="the-wide-camera-malfunction-case-c3x"></a>
### C3X의 와이드 카메라 오작동 사례

**증상**:

* “Camera Malfunction, wideRoadCamera”
* “Camera Frame Rate Low, Reboot Your Device”

**해결 방법**:

[카메라 오작동 사례 (C3)](#the-camera-malfunction-case-c3)와 달리, C3X에서는 camera가 main board에 납땜되어 있어 이 문제를 고치기가 매우 어렵습니다.

선택지는 제한적이고, 그중 하나도 썩 좋지는 않습니다.

* SOM 다시 장착(해결 가능성 20%)
* [Hack: wide camera 사용 비활성화](https://discord.com/channels/469524606043160576/871838269405556736/1399198229861634098)
  * 이것은 분명히 무언가를 cripple하지만, 아무것도 없는 것보다는 낫습니다.

**예시**:

* [prabh123의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1399198229861634098)
  * [jyoung8607의 log analysis](https://discord.com/channels/469524606043160576/871838269405556736/1398377902051164170)
    * “route를 살펴봤습니다. ecamera에서 image는 얻고 있지만 간헐적으로만 들어옵니다. **현재 upstream openpilot에서 이것을 재현할 수 있을 때에만** 실제 image sensor는 괜찮다고 추측하겠습니다. 하지만 네 개의 CSI data transfer lane 중 하나가 drop out되고 있는 것으로 의심됩니다. 최선의 선택지는 아마 comma의 out-of-warranty flat rate repair service일 것입니다. 최근 camera support code에 매우 큰 변화가 있었고, 이 가설은 잠재적으로 오래된 fork를 실행하는 동안에는 **적용되지 않습니다**.”
  * SOM을 다시 장착해도 작동하지 않았습니다.
  * 문제 해결을 위해 sunnypilot에서 wide camera를 비활성화하는 hack을 선택하고 만들었습니다. 여전히 작동합니다.
    * “네, 솔직히 말하면 highway에서도 똑같습니다. 도로에서 right turn은 더 나쁘지만, 어차피 원래도 좋았던 적이 없습니다. 우리는 turn에서는 항상 Pause Lateral을 쓰니까 괜찮습니다.”

<a id="the-bad-step-down-dcdc-regulator-case"></a>
### Step-down DC/DC 레귤레이터 불량 사례

**증상**:

* 동작이 [퓨즈가 나간 사례](#the-blown-fuse-case)와 비슷합니다.
* 퓨즈 측정에서 ground short가 나옵니다.
* [퓨즈 자체는 양호합니다.](#the-blown-fuse-case)
* thermal camera로 특정 chip이 short의 원인으로 식별됩니다.

![Regulator and Thermal Camera View](https://github.com/user-attachments/assets/be2e76e0-cf4f-4b3e-ab10-6687a16dae46)


**진단**:

퓨즈에서 ground short가 감지되었습니다. 퓨즈를 제거한 뒤, short는 step-down buck regulator chip으로 추적되었습니다. diode side의 VN side에 1V를 주입하고 thermal camera를 사용해 short를 이 chip까지 추적했습니다. buck regulator를 제거하자 short는 더 이상 존재하지 않았습니다.

**해결 방법**:

고장난 SY8368AQQC chip을 교체하세요. 다만 3x3mm QFN3x3-12 package라 매우 빡빡합니다.

Datasheet: https://www.lcsc.com/datasheet/C207642.pdf

안타깝게도 이 사례에서 아직 성공적인 수리가 있었던 것 같지는 않습니다. 성공했다면 여기에 알려 주세요.

**판매처**:

* 선호하는 전자 부품 vendor에서 SY8368AQQC를 검색하면 됩니다. 마지막 3글자는 date code일 뿐이라 달라질 수 있습니다.

**추가 참고**:

새 MCU의 MOSFET을 태우지 않으려면 “L” inductor의 integrity도 함께 확인하는 것이 권장됩니다.

**예시**:

* [ZUM(zum114)의 C3X 🛑](https://discord.com/channels/469524606043160576/871838269405556736/1423032049136173056)
  * [Initial Post](https://discord.com/channels/469524606043160576/871838269405556736/1422027156829241386)
  * [“buck chip의 thermal cam 짧은 영상”](https://discord.com/channels/469524606043160576/871838269405556736/1423040186769608857)
  * [“이런, 같은 chip이 또 터졌으니 포기합니다”](https://discord.com/channels/469524606043160576/871838269405556736/1426776980443107328)

<a id="the-bad-power-ic-mp1701-case"></a>
### 전원 IC (MP1701) 불량 사례

**증상**:

* 부팅되지 않습니다.

**해결 방법**:

_작성 중_

* 고장난 MP1701 chip을 교체합니다.

**예시**:

* [Drago 고객의 C3X](https://discord.com/channels/469524606043160576/871838269405556736/1469159211446304912)

<a id="comma-four-c4"></a>
## comma four (C4)

출시: 2025-11-08

Codename: mici

https://blog.comma.ai/comma-four/

comma four는 [COMMA_CON 2025](https://www.reddit.com/r/Comma_ai/comments/1nr5zvn/comma_con_2025/)에서 발표되었습니다.

comma의 첫 주요 form factor redesign입니다. 앞유리에 붙는 큰 landscape phone 형태 대신, 이제는 작은 windshield dashcam처럼 생겼고 radar detector display 정도 크기의 훨씬 작은 touch GUI display가 있습니다.

[일부 사양은 다음과 같습니다](https://discord.com/channels/469524606043160576/1436852432503046294/1437501443253866558):

* 작은 form factor.
* OLED touchscreen (536x240).
* 업그레이드된 speaker.
* Noctua fan 및 더 나은 thermal design 같은 강화된 cooling system이 있는 Snapdragon 845.
* SOM과 Red Panda(C3X에서 이어짐)가 이제 같은 board 위에 있습니다.
* camera는 별도 board에 있습니다.
* 전원 안정성 향상을 위해 supercapacitor가 없습니다.
* 이후 C3와 C3X에서 삭제되었던 u-blox GPS module이 다시 도입되었습니다.
* onboard eSIM이 physical SIM slot을 대체합니다. 다만 board에는 physical SIM slot이 여전히 존재하지만 접근하려면 기기 상단을 떼어내야 합니다.
  * 한 번에 하나만 사용할 수 있습니다. 둘 다 있으면 회로가 전환되어 removable SIM을 우선합니다.
  * embedded eSIM은 이전 comma 기기에서 사용되던 removable eSIM 또는 UICC를 대체합니다.
* 야간 성능이 개선된 3x OS04C10 camera.
* 즉시 경화 adhesive를 사용하는 새 mount.
  * 접착력을 높이기 위해 windshield와 닿는 표면적이 더 넓습니다.
  * 더 가볍습니다.
* storage는 여전히 128GB이지만, camera가 [더 작은 file size](https://github.com/commaai/openpilot/blob/master/system/loggerd/loggerd.h#L37-L42)로 기록해 더 긴 녹화 시간을 제공합니다.
* 새로운 flexible OBD-C cable.
* [다른 modem](https://discord.com/channels/469524606043160576/1436852432503046294/1456178902224474142)
* 더 높은 신뢰성을 위해 부품 수가 줄었습니다.

<a id="the-cable-not-plugged-in-all-the-way-case-c4"></a>
### 케이블이 끝까지 꽂히지 않은 사례 (C4)

**증상**:

* 차량을 식별할 수 없습니다.
  * 예: “Please submit a pull request to add the firmware versions to the proper vehicle”가 뜨지만, 이전 comma 기기에서는 hack이나 forcing 없이 작동했습니다.
* CAN BUS error가 발생합니다.
* 차량이 on-road mode로 들어가지 않습니다.
* “Check Hardware” 또는 비슷한 error가 발생합니다.
* comma가 동봉한 새 straight cable이 아니라 오래된 각진 C3 또는 C3X cable을 사용했습니다.

**해결 방법**:

**comma의 새 케이블을 사용하고 더 세게 밀어 넣으세요.**

comma four용 새 OBD-C cable은 곧은 형태이며, 제대로 seated되었는지 바로 알아차리기 어렵습니다. 더 세게 밀어 넣으면 제대로 seated됩니다.

이렇게 보여야 합니다.

![Cable inserted](https://github.com/user-attachments/assets/e3da361e-626c-4b25-ab96-ac3f6ac96b66)

C3 또는 C3X에서 사용하던 90도 OBD-C cable을 사용하면 안 됩니다. 각진 끝은 이 용도로 설계되지 않았고 맞지 않습니다.

> [!TIP]
> 순정 C4 cable은 straight-straight 형태이므로, 각진 연결을 원할 수 있습니다. Erich는 순정 cable과 함께 사용할 때 [이 특정 각진 USB-C extension](https://amzn.to/4oYG6DS)이 잘 작동한다고 확인했습니다.

여전히 문제가 있다면, harness-box 쪽은 [OBD-C 케이블이 하네스 박스에 완전히 꽂히지 않은 사례](#the-not-fully-inserted-obd-c-cable-into-harness-box-case)를 보고, 실제 cable fault는 [OBD-C 케이블 불량 사례](#the-bad-obd-c-cable-case)를 확인하세요.

**예시**:

* [mau.maumau의 C4](https://discord.com/channels/469524606043160576/524592892627517450/1448050351243657348)
  * 끝까지 들어가 있지 않았습니다.
  * 위의 올바른 cable 사진은 mau.maumau가 제공했습니다.
* [livinginkaos의 C4](https://discord.com/channels/469524606043160576/1436852432503046294/1450975123157815477)
  * “3x에서 업그레이드했습니다 - 90 deg short cable을 사용했다면”
* [caliber224의 C4](https://discord.com/channels/469524606043160576/524327905937850394/1451785137195843747)
  * Radar state error / airbag warning light
* [daanigator_75882의 C4](https://discord.com/channels/469524606043160576/524327905937850394/1468465889614631028)
  * “화면이 검습니다.”
  * “감사합니다. 꽂을 때 제가 너무 조심스러웠던 것으로 드러났습니다. 이번에는 정말 세게 밀어 넣었고 작동합니다!!”
* [janxman.의 C4](https://discord.com/channels/469524606043160576/524592892627517450/1496206614313697380)
  * cable을 완전히 seated하려면 조금 더 힘이 필요했습니다.
  * 끝까지 들어가자 기기가 calibration percentage를 표시하기 시작했습니다.

<a id="see-also"></a>
# 함께 보기

* https://docs.comma.ai/concepts/glossary/ - 공식 용어집

[cdiscord]: https://discord.comma.ai/
[on-road]: https://docs.comma.ai/concepts/glossary/#onroad
[comma connect]: https://docs.comma.ai/concepts/glossary/#comma-connect
[Panda]: https://docs.comma.ai/concepts/glossary/#panda
