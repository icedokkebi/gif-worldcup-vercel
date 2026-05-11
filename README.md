# GIF 이상형 월드컵 (Vercel Edition)

영화 대사 GIF로 하는 이상형 월드컵 게임 - 정적 사이트 버전

## 특징

- 🎬 **500개의 영화 GIF** (10개 카테고리 × 50개)
- 🏆 **토너먼트 시스템** (16강, 32강 지원)
- 📊 **랭킹 시스템** (승률 기반)
- 💾 **로컬 저장** (브라우저 localStorage 사용)
- ⚡ **완전 정적** (백엔드 없음, Vercel 무료 배포 가능)

## 카테고리

- reaction (리액션)
- agree (동의)
- hype (신남)
- confusion (혼란)
- emotion (감정)
- thinking (생각중)
- greeting (인사)
- scared (무서움)
- angry (화남)
- insult (모욕)

## 데이터 크기

- GIF 파일: 944MB
- 총 파일 수: 500개
- 카테고리당: 50개

## Vercel 배포 예상 사용량

**월드컵 1회 플레이 (16강):**
- 15번 대결 × 2개 GIF = 30개 로드
- 평균 크기: ~48MB per session

**Vercel 무료 플랜 (100GB/월):**
- 약 2,000명 이용 가능
- CDN 캐싱으로 실제로는 더 많음

## 로컬 테스트

간단한 HTTP 서버로 테스트:

```bash
# Python
python -m http.server 8000

# Node.js
npx serve

# PHP
php -S localhost:8000
```

브라우저에서 `http://localhost:8000` 접속

## Vercel 배포

### 방법 1: Vercel CLI

```bash
npm install -g vercel
vercel
```

### 방법 2: GitHub 연동

1. GitHub 레포지토리 생성
2. 코드 푸시:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin YOUR_REPO_URL
   git push -u origin main
   ```
3. [vercel.com](https://vercel.com)에서 Import
4. 자동 배포 완료!

## 프로젝트 구조

```
gif-worldcup-vercel/
├── index.html              # 메인 HTML (모든 CSS/JS 포함)
├── vercel.json            # Vercel 설정
├── public/
│   ├── data.json          # GIF 메타데이터
│   └── gifs/              # GIF 파일들
│       ├── reaction/
│       ├── agree/
│       ├── hype/
│       └── ...
└── README.md
```

## 데이터 구조

### data.json

```json
{
  "categories": [
    {"name": "reaction", "count": 50}
  ],
  "clips": [
    {
      "id": 1,
      "category": "reaction",
      "filename": "gif_12345_Movie_Title",
      "movie_title": "Movie Title",
      "gif_url": "/gifs/reaction/gif_12345_Movie_Title.gif"
    }
  ]
}
```

### localStorage

- `gif_wc_player_id`: 플레이어 UUID
- `gif_wc_votes`: 투표 히스토리
- `gif_wc_championships`: 우승 기록

## 기술 스택

- Vanilla JavaScript (No frameworks)
- localStorage API
- Fetch API
- CSS Grid & Flexbox

## 원본 프로젝트

이 프로젝트는 FastAPI 백엔드 버전을 정적 사이트로 변환한 것입니다.
원본: `/mnt/d/projects/gif-worldcup`

## 라이선스

MIT
