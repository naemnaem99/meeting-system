---
name: meeting-cal
description: Notion 회의록에서 내 액션 아이템을 읽어 Google Calendar에 등록. 트리거: /meeting-cal, "캘린더 등록", "내 할 일 캘린더에"
---

## 회의록 → 캘린더 등록 스킬

### 팀 정보
- **팀원:** 소정, 하영, 해냄, 유진
- **Notion DB:** `collection://de7bdeac-d0b4-821e-96c7-0704ab267ee1` (HANCOM D조_한컴 > 1.회의록)

---

### 1단계: 사용자 확인

사용자에게 묻는다:

```
이름이 뭐예요? (소정 / 하영 / 해냄 / 유진)
어떤 회의록을 볼까요? (날짜 입력 또는 "최신"으로)
```

---

### 2단계: Notion 회의록 가져오기

`mcp__claude_ai_Notion__notion-search` 로 회의록 DB에서 해당 날짜(또는 최신) 페이지 검색.

검색 안 되면 `mcp__claude_ai_Notion__notion-fetch` 로 DB 직접 조회:
- URL: `https://app.notion.com/p/716bdeacd0b482adae4f81a1be299bd7`

페이지 찾으면 `mcp__claude_ai_Notion__notion-fetch` 로 전체 내용 가져오기.

---

### 3단계: 내 액션 아이템 추출

페이지 본문의 "액션 아이템" 테이블에서 **담당자 = 1단계에서 입력한 이름**인 행만 추출.

각 항목:
- 할 일 (내용)
- 기한 (날짜 or "미정")

---

### 4단계: Google Calendar 등록

`mcp__claude_ai_Google_Calendar__create_event` 로 기한이 있는 항목만 등록:

```
summary: [할 일 내용]
allDay: true
startTime: YYYY-MM-DDT00:00:00+09:00  ← 기한 날짜
endTime:   YYYY-MM-DDT00:00:00+09:00  ← 동일
timeZone: "Asia/Seoul"
description: "회의록: [Notion 페이지 URL]"
```

기한 "미정" 항목 → 캘린더 등록 건너뜀.

---

### 5단계: 완료 보고

```
✅ 캘린더 등록됨:
- [할 일] — [날짜]

⚠️ 기한 미정 (미등록):
- [할 일]
```
