# 배포 가이드 (GitHub + Cloudflare Pages)

## 1. GitHub
1. github.com → New repository (예: `gamejob-site`, Public)
2. 이 폴더의 **모든 파일**(index.html, free/, pdf/, site-config.json, favicon.svg, og.png, robots.txt, 404.html, privacy.html)을 "uploading an existing file"로 업로드 → Commit
   (`*.py`, `_pdf_src`, `page*.html`, `__pycache__`는 올리지 않아도 됨)

## 2. 호스팅 (트래픽 무료·무제한)
- Cloudflare Pages: Workers & Pages → Create → Pages → Connect to Git → 저장소 선택
  Build command 비움 / Output directory `/` → Deploy. 이후 GitHub에 커밋하면 자동 반영.
- 대안: GitHub Pages (Settings → Pages → Branch: main / root)

## 3. 짧은 주소 (폴더 방식, 설정 불필요)
- /free/01/ · /free/02/ · /free/03/ · /free/04/ · /free/05/ · /free/sample/

## 4. PDF 다운로드 버튼 켜고 끄기
GitHub에서 `site-config.json` 열기 → 연필(Edit) → 값 변경 → Commit
- 켜기: `{ "pdfDownload": true }`  / 끄기: `{ "pdfDownload": false }`
- PDF 파일은 `pdf/` 폴더에 있음 (파일 교체 가능)

## 5. 도메인 있을 때 (SEO·분석)
빌드 시 환경변수: SITE_URL, GA_ID, GSC_VERIFY, NAVER_VERIFY → `python3 build.py`
(값을 알려주면 대신 빌드해 드립니다)
