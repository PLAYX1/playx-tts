# playx-tts

PLAY X 앱들이 같이 쓰는 음성 합성(TTS) 모델 파일 보관소입니다. 앱은 필요할 때 한 번 내려받아 폰 안에서 씁니다.
이 저장소에는 앱 코드가 없습니다. 파일은 **Releases** 에 있습니다.

## 어느 릴리스를 쓰나요

| 릴리스 | 크기 | 상태 |
|---|---|---|
| **supertonic-3-v2** | 약 181MB | **정상본. 앱은 이것만 받습니다.** |
| supertonic-3 | 약 105MB | **쓰지 마세요.** 소리를 만드는 부분(보코더)까지 압축해서 목소리가 깨져 들립니다. (삭제 예정) |
| v1 | 작음 | 처음 올린 목소리 파일. 이미 나간 앱이 쓸 수 있어 남겨 둡니다. |

## supertonic-3-v2

- 모델: **Supertonic 3** — 만든 곳 Supertone Inc. · https://huggingface.co/supertone-oss-archive/supertonic-3
- 이것은 PLAY X 가 만든 모델이 아닙니다. 위 모델에서 소리를 만드는 부분(보코더)은 **원본(fp32) 그대로** 두고, 나머지 신경망만 8비트로 압축(onnxruntime `quantize_dynamic`, QUInt8)한 뒤 45MB 이하 조각으로 나눈 것입니다.
- 목소리 10개: 여성 F1~F5, 남성 M1~M5. 모델 본체는 모두 같이 쓰고, 목소리 파일은 각각 약 290KB 입니다.
- 받는 주소: `https://github.com/PLAYX1/playx-tts/releases/download/supertonic-3-v2/<파일 이름>`
- `manifest.json` 에 파일 목록·크기·SHA256 이 있습니다. 파일 이름의 `__` 는 폴더 구분입니다(`onnx__vocoder.onnx.part000` → `onnx/vocoder.onnx`). 큰 파일은 `.part000`, `.part001` 순서로 이어 붙입니다.
- 이어받기(Range)가 됩니다.

## 라이선스

OpenRAIL-M — `LICENSE` 파일을 그대로 두었습니다. 사용 제한과 출처 표시를 이어받습니다.
이 모델로 만든 소리를 앱에서 보여 줄 때는 「AI 음성」 표시와 출처(Supertonic 3 · Supertone)를 함께 적습니다.

## 캐릭터 목소리 설정 (presets/)

PLAY X 앱의 캐릭터 목소리는 새 음성 파일이 아니라 위 모델의 목소리(F1~F5, M1~M5)에 속도·쉼 같은 설정을 붙인 것입니다.
설정 파일은 Releases 가 아니라 이 저장소의 `presets/` 폴더에 있습니다.

- `presets/ravi.json` — 레이븐볼트 라비(F1 · 합성 속도 0.908 · 재생 속도 ×1.1553)
- `presets/commulearn.json` — 커뮤런 캐릭터 26명(목소리·속도·쉼)

앱은 이 설정과 `supertonic-3-v2` 모델(또는 이후 릴리스)을 함께 받아 씁니다. 사람이 말하는 것처럼 들리더라도 AI 음성이므로 앱 화면에 「AI 음성」 표시를 붙입니다.
