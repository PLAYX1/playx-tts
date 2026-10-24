# whisper (음성 인식 모델 보관)

브라우저에서 받아 쓰는 Whisper 모델 사본. 파일 하나가 50MB 이하여야 jsDelivr 로 받을 수 있다
(`https://cdn.jsdelivr.net/gh/PLAYX1/playx-tts@main/whisper/tiny/...`, CORS 허용).

| 폴더 | 원본 | 용량 | 비고 |
|---|---|---|---|
| tiny | onnx-community/whisper-tiny (양자화 ONNX) | 약 41MB | 한국어 정확도 보통. 키오스크에서 인식률 측정 필요 |

- 원본 Whisper(OpenAI)는 MIT 라이선스. 변환본(onnx-community)의 라이선스 표기는 원 저장소를 따른다.
- **jsDelivr 는 GitHub 파일이 20MB 를 넘으면 403** 이라 tiny 디코더(30.7MB)는 16MB 조각 둘(`decoder_model_merged_quantized.onnx.part00/01`)로 올렸다. 받은 뒤 순서대로 이어 붙이고 `decoder.sha256` 으로 검증한다.
- base(약 77MB)는 디코더가 53.7MB 라 50MB 한도를 넘는다 — 쓰려면 쪼개거나 다른 곳에 둔다.
- 앱은 사용자가 「받기」를 눌러야만 받는다(자동 다운로드 금지).
