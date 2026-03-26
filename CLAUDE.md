# 이미지 압축 도구

브라우저에서 동작하는 순수 클라이언트 사이드 이미지 압축 도구입니다. 서버 없이 HTML/JS만으로 구성되어 있습니다.

## 프로젝트 구조

```
pic_zip/
└── index.html   # 앱 전체 (HTML + CSS + JS 단일 파일)
```

## 주요 기능

- 폴더 또는 파일 드래그 앤 드롭 / 선택
- 지정한 최대 파일 크기(MB) 이하로 자동 압축
- JPG, PNG, BMP, WebP 지원
- 투명도(alpha) 감지 → PNG/JPEG 자동 선택
- 압축 결과를 ZIP으로 일괄 다운로드 (외부 라이브러리 없음)

## 기술 스택

- 순수 HTML/CSS/JavaScript (프레임워크 없음)
- `Canvas API` — 이미지 리사이즈 및 재인코딩
- `CompressionStream('deflate-raw')` — ZIP 빌드 (Chrome 80+, Firefox 113+, Safari 16.4+)
- 미지원 브라우저는 무압축(STORE) 방식으로 폴백

## 개발 가이드

- 단일 `index.html` 파일로 유지할 것 (빌드 도구 불필요)
- 외부 라이브러리 추가 금지 — 오프라인/CDN 없이도 동작해야 함
- XSS 방지: 파일명 출력 시 `textContent` 사용 (`innerHTML` 금지)

## 배포

GitHub Pages (`main` 브랜치 root) 자동 배포.
URL: `https://koga1694.github.io/image-compressor/`
