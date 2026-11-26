# 10분 키즈뉴스 — 랜딩 페이지

7세~초등 4학년 아이를 위한 하루 한 장 뉴스 학습지의 무료 샘플 랜딩.
`https://10minkids.com` 으로 서비스한다.

- `index.html` — 페이지 전부. 외부 라이브러리 없음
- `fonts.css` + `fonts/` — Jua · Gowun Dodum (구글 폰트 OFL 자체 호스팅)
- `img/` — 실제 지면 이미지
- `CNAME` — GitHub Pages 사용자 지정 도메인
- **파비콘** (2026-11-26 추가) — `favicon.svg` · `favicon.ico` · `apple-touch-icon.png`
  · `icon-192.png` · `icon-512.png` · `site.webmanifest`

### 파비콘은 손으로 만들지 않는다
전부 **`seamanse21/jey-tools` 의 `brand/`** 에서 뽑은 것이다.
`favicon.svg` 는 `brand/profile.svg` 를 그대로 복사했고, PNG 들은
`brand/profile-1080.png` 을 줄인 것이다. **브랜드 그림이 바뀌면 거기서 다시 뽑는다.**

```bash
cd 저장소/10minkids
cp ../jey-tools/brand/profile.svg favicon.svg
python3 -c "
from PIL import Image
s=Image.open('../jey-tools/brand/profile-1080.png').convert('RGB')
for n,z in [('apple-touch-icon.png',180),('icon-192.png',192),('icon-512.png',512)]:
    s.resize((z,z), Image.LANCZOS).save(n, optimize=True)
s.resize((256,256), Image.LANCZOS).save('favicon.ico', sizes=[(16,16),(32,32),(48,48)])
"
```

세 쪽(`index.html` · `buy/` · `thanks/`) 의 `<head>` 에 같은 5줄이 들어 있다.
`theme-color` 는 브랜드 주황 `#f08c2e` — 모바일 브라우저 주소창이 그 색으로 물든다.

원본과 작업 메모는 `seamanse21/jey-tools` 의 `landing/` 에 있다.
