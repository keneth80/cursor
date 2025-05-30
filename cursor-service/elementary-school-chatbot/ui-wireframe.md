# UI 와이어프레임 (기획 기반 텍스트 구성)

# ✅ 1. UI 와이어프레임

## 1) 메인 화면

상단: 앱 로고 + 챗봇 캐릭터

중앙: 대화 시작 버튼 (말풍선 형태)

하단 메뉴:

💬 대화하기

🌱 오늘의 미션

🏆 칭찬스티커

📚 이야기방

⚙️ 설정

## 2) 대화 화면

상단: 챗봇 캐릭터 이름 + 표정 애니메이션

중앙: 대화창 (텍스트 + 음성 출력)

입력창: 아이가 텍스트 or 음성 선택 가능

하단 버튼:

🎭 역할극 모드

❓ 궁금해요 모드

## 3) 오늘의 미션

카드 UI로 일일/주간 미션 표시

미션 예시:

[✔️] 오늘 친구에게 칭찬하기

부모님께 고마움 전하기

미션 완료 시 애니메이션 + 스티커 보상

## 4) 칭찬 스티커

모은 스티커 도감

인성 덕목별 뱃지 카테고리:

정직 / 배려 / 존중 / 책임감 등

캐릭터 레벨업 애니메이션

## 5) 이야기방

동화 / 상황극 리스트

캐릭터별 스토리 분류

음성 + 애니메이션 효과 동화 재생

# ✅ 2. DB 설계 (기본 테이블 구조)

## 1) Users

| 필드명     | 타입     | 설명               |
| ---------- | -------- | ------------------ |
| user_id    | UUID     | 유저 고유 ID       |
| nickname   | STRING   | 아이가 설정한 이름 |
| age        | INT      | 나이               |
| level      | INT      | 레벨               |
| created_at | DATETIME | 가입일             |

## 2) Missions

| 필드명      | 타입   | 설명              |
| ----------- | ------ | ----------------- |
| mission_id  | UUID   | 미션 ID           |
| title       | STRING | 미션 제목         |
| description | TEXT   | 미션 설명         |
| type        | STRING | 'daily', 'weekly' |
| reward_type | STRING | 스티커, 경험치 등 |

## 3) UserMissions

| 필드명       | 타입     | 설명      |
| ------------ | -------- | --------- |
| user_id      | UUID     | 유저 ID   |
| mission_id   | UUID     | 미션 ID   |
| status       | BOOLEAN  | 완료 여부 |
| completed_at | DATETIME | 완료 시간 |

## 4) Dialogues

| 필드명       | 타입     | 설명               |
| ------------ | -------- | ------------------ |
| dialogue_id  | UUID     | 대화 ID            |
| user_id      | UUID     | 유저 ID            |
| message      | TEXT     | 사용자의 질문/답변 |
| bot_response | TEXT     | 챗봇의 응답        |
| created_at   | DATETIME | 대화 시간          |

## 5) Stickers

| 필드명     | 타입   | 설명              |
| ---------- | ------ | ----------------- |
| sticker_id | UUID   | 스티커 ID         |
| name       | STRING | 스티커 이름       |
| image_url  | STRING | 이미지 경로       |
| category   | STRING | '정직', '배려' 등 |

## 6) Stories

| 필드명   | 타입   | 설명                 |
| -------- | ------ | -------------------- |
| story_id | UUID   | 동화 ID              |
| title    | STRING | 제목                 |
| content  | TEXT   | 본문 (또는 음성 URL) |
| category | STRING | '정직', '협동' 등    |

# ✅ 3. 챗봇 시나리오 스크립트 예시

시나리오 1: 정직에 대한 대화

```
User: 오늘 친구랑 싸웠어요...
Bot: 어떤 일이 있었는지 말해줄 수 있어?
User: 내가 친구 물건을 망가뜨렸는데 말 안 했어요.
Bot: 용기 내줘서 고마워! 실수는 누구나 할 수 있어. 정직하게 말하는 것이 진짜 용기 있는 행동이야.
Bot: 혹시 친구에게 어떻게 사과하면 좋을지 같이 연습해볼까?
```

시나리오 2: 역할극 모드

```
Bot: [상황극 시작!] 친구가 넘어졌어요. 너는 어떻게 할래?
(선택지)
1. 그냥 지나간다.
2. 괜찮냐고 묻고 도와준다.
→ 2번 선택 시:
Bot: 잘했어! 배려는 친구를 생각하는 마음에서 시작돼.
칭찬 스티커 [배려곰돌이] 획득! 🎉
```

시나리오 3: 감정 표현 훈련

```
Bot: 오늘 기분은 어땠어?
User: 좀 속상했어요.
Bot: 그런 날도 있지. 왜 속상했는지 말해줄래?
User: 친구가 내 얘기를 무시했어요.
Bot: 그랬구나... 마음이 많이 아팠겠다. 그럴 땐 “나는 속상해”라고 말해보는 것도 좋아.
Bot: "나는 속상했어, 왜냐하면 내 말을 들어주지 않아서야" 이렇게 말해볼까?
```
