# 🗂️ 프로젝트 템플릿 디렉토리 구조 예시

```
project-template/
├── 📁 docs/
│   ├── 01_기획서.md
│   ├── 02_기능정의서.md
│   ├── 03_화면설계_와이어프레임.md
│   ├── 04_챗봇_시나리오.md
│   ├── 05_DB_설계서.md
│   ├── 06_API_스펙.md
│   ├── 07_코드_가이드라인.md
│   └── README.md
│
├── 📁 frontend/
│   ├── 📁 public/
│   ├── 📁 src/
│   │   ├── 📁 components/
│   │   ├── 📁 pages/
│   │   ├── 📁 hooks/
│   │   ├── 📁 lib/
│   │   ├── 📁 styles/
│   │   └── index.tsx
│   ├── .env.example
│   ├── next.config.js
│   ├── tailwind.config.ts
│   └── package.json
│
├── 📁 backend/
│   ├── 📁 app/
│   │   ├── main.py
│   │   ├── routers/
│   │   ├── services/
│   │   ├── schemas/
│   │   └── utils/
│   ├── requirements.txt
│   └── serverless.yml (AWS Lambda + API Gateway 배포용)
│
├── 📁 infra/
│   ├── main.tf
│   ├── variables.tf
│   └── README.md
│
├── 📁 chatbot/
│   ├── prompts/
│   ├── scenarios/
│   └── memory/
│
├── .gitignore
├── README.md
└── LICENSE

```

# 📑 주요 문서 파일명 설명

| 파일명                        | 설명                                           |
| ----------------------------- | ---------------------------------------------- |
| `01_기획서.md`                | 전체 서비스 개요 및 방향                       |
| `02_기능정의서.md`            | 상세 기능 목록 및 흐름                         |
| `03_화면설계_와이어프레임.md` | Figma나 스케치 기반 화면 설명                  |
| `04_챗봇_시나리오.md`         | 인성 교육 챗봇의 대화 시나리오                 |
| `05_DB_설계서.md`             | 사용자/로그/챌린지/보상 관련 데이터베이스 설계 |
| `06_API_스펙.md`              | 프론트와 백엔드 간 통신 규약 (REST/GraphQL 등) |
| `07_코드_가이드라인.md`       | 팀 코드 스타일, 폴더 구조, 커밋 규칙 등        |

# ✅ 추천 기술 스택

| 구분       | 기술                                                |
| ---------- | --------------------------------------------------- |
| 프론트엔드 | Next.js + TypeScript + TailwindCSS                  |
| 백엔드     | FastAPI + AWS Lambda (Serverless Framework)         |
| AI 연동    | OpenAI API (ChatGPT, embeddings 등)                 |
| 인증       | Firebase Auth 또는 Cognito                          |
| DB         | DynamoDB or PostgreSQL (RDS)                        |
| 배포       | Vercel (프론트) + Lambda (백엔드) + Terraform (IaC) |

# ▶️ 초기 커맨드 (예시)

```
cd project-template/frontend
npm install

cd ../backend
pip install -r requirements.txt

cd ../infra
terraform init

```
