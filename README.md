# 하나님의 음성 · 자연스러운 목소리 파일

하나님의 음성 앱이 「설정 > 자연스러운 목소리」에서 한 번 내려받는 음성 합성 모델 묶음입니다.
이 저장소에는 앱 코드가 없습니다. 파일은 Releases 에 있습니다.

- 모델: Supertonic 3 (Supertone Inc.) — https://huggingface.co/supertone-oss-archive/supertonic-3
- 이 묶음은 위 모델을 8비트로 압축(onnxruntime quantize_dynamic, QUInt8)하고 45MB 이하 조각으로 나눈 것입니다.
- 라이선스: OpenRAIL-M (LICENSE 파일). 앱에는 「AI 음성」 표시와 출처를 적어 두었습니다.
- 파일 이름의 `__` 는 폴더 구분입니다. 예: `onnx__vocoder.onnx.part000` → `onnx/vocoder.onnx`
