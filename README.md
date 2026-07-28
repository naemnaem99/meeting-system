# D조 회의록 자동 정리 시스템

회의 내용을 자동으로 구조화하고 Notion에 저장, 완료 상황을 자동 추적하는 Claude Code 플러그인입니다.

---

## 🎯 기능

### `/meeting` — 회의록 작성
- 회의 내용 입력 → 자동으로 구조화
- 결정사항, 액션 아이템 (담당자·할 일·기한·상태), 논의 내용
- Notion D조_한컴 > 1.회의록 DB에 자동 저장

### `/meeting-cal` — 캘린더 등록
- Notion 회의록에서 본인 담당 항목만 추출
- 기한이 있는 일정을 Google Calendar에 추가
- 캘린더는 마감일 상기용 (진행은 Notion에서 추적)

### `/meeting-check` — 완료 표기
- 완료한 업무 입력 → Notion 상태 자동 "완료 ✅"
- 진행 상황을 실시간으로 팀에 공유

---

## ⚡ 빠른 시작

### 사전 설정 (처음 1회)

1. **Claude Code 설정 열기** → Integrations
2. **Notion MCP 연결** (HANCOM 워크스페이스 선택 ⭐)
3. **Google Calendar MCP 연결**
4. **플러그인 설치:**
   ```bash
   npx skills add <repository-url>
   ```

### 첫 사용

**회의 후:**
```
/meeting
→ 회의 내용, 날짜, 참석자 입력
→ Notion 자동 저장 (상태: 미정) ✅
```

**각 팀원이:**
```
/meeting-cal
→ 본인 이름, 회의록 선택
→ Google Calendar에 마감일 추가 ✅
```

**진행 중:**
```
/meeting-check
→ 완료한 일 입력
→ Notion 상태 자동 업데이트 (완료 ✅)
```

---

## 📖 상세 가이드

- **[회의록 작성 (`/meeting`)](./meeting/README.md)** — 회의 정리 담당자용
- **[캘린더 등록 (`/meeting-cal`)](./meeting-cal/README.md)** — 마감일 알림용
- **[완료 표기 (`/meeting-check`)](./meeting-check/README.md)** — 진행 상황 추적용
- **[팀 종합 가이드](../meeting-system-guide.md)** — 전체 workflow 설명

---

## 📋 포함된 스킬

| 스킬 | 역할 | 사용자 |
|------|------|--------|
| `meeting` | 회의 내용 정리 → Notion 저장 | 회의 정리 담당자 1명 |
| `meeting-cal` | 액션 아이템 → 개인 캘린더 등록 | 각 팀원 |
| `meeting-check` | 완료한 일 표기 → Notion 상태 업데이트 | 각 팀원 |

---

## 🔧 요구사항

- **Claude Code** 최신 버전
- **Notion MCP** (HANCOM 워크스페이스 연결)
- **Google Calendar MCP**

---

## 👥 팀원

소정, 하영, 해냄, 유진

---

## 💬 피드백 & 개선

첫 사용 후 개선사항이 있으면 공유해주세요:
- 추가 기능 요청
- 불편한 부분
- 버그 리포트

---

## 📄 라이선스

MIT
