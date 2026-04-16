# BLUELADY CALENDAR 🩵

> 노션 DB와 연동되는 블루레이디 수입 관리 캘린더 위젯

블루레이디 협찬 · 체험단 · RT이벤트 일정을 노션에서 캘린더로 한눈에 확인할 수 있는 위젯이에요.

made with 🩵 by [heev](https://x.com/heevtoday)

---

## 미리보기

- 월별 캘린더 뷰
- 일정 클릭 시 상세 보기
- 유형별 배지 (협찬 / 체험단 / RT이벤트 / 기타)
- 진행중 일정 핑크 강조 표시
- 노션 임베드 최적화

---

## 설치 가이드

### 시작 전에 필요한 것

- GitHub 계정
- Vercel 계정 (vercel.com에서 GitHub 로그인)
- 노션 계정

---

### STEP 1 — 레포 Fork하기

이 레포 오른쪽 상단 **Fork** → **Create fork** 클릭

---

### STEP 2 — Vercel에 배포하기

1. `vercel.com` → **Add New Project**
2. Fork한 `bluelady-calendar` 레포 선택 → **Import**
3. 설정 건드리지 말고 **Deploy**
4. 내 고유 URL 생성됨 (예: `bluelady-calendar-xxx.vercel.app`) ✓

---

### STEP 3 — 노션 인테그레이션 만들기

1. `notion.so/my-integrations` 접속
2. **New integration** → 이름 입력 → **Submit**
3. **Internal Integration Secret** 복사해서 메모장에 저장 ✓

---

### STEP 4 — 노션 DB에 인테그레이션 연결

1. 연결할 노션 DB 페이지 열기
2. 오른쪽 상단 **···** → **연결 추가** → 인테그레이션 선택 ✓

---

### STEP 5 — DB ID 찾기 ⚠️

> 노션 앱이 아니라 **웹 브라우저**에서 열어야 해요

1. DB 오른쪽 상단 **↗ (전체 페이지로 열기)** 클릭
2. URL에서 ID 복사

```
notion.so/워크스페이스/여기가DBID?v=뷰아이디
                      ↑ ?v= 앞까지만 복사
```

> ⚠️ DB 자체를 전체 페이지로 열었을 때의 URL이어야 해요.
> 잘못된 ID를 넣으면 `page, not a database` 오류가 나요.

---

### STEP 6 — 온보딩 페이지에서 설정

1. `https://calendar2-dujp.vercel.app/onboarding` 접속
2. **NOTION_TOKEN** — STEP 3 시크릿 키 입력
3. **NOTION_DB_ID** — STEP 5 DB ID 입력
4. 속성 이름 입력 (기본값 그대로면 비워두기)
5. **설정 완료** → **환경변수 전체 복사** ✓

---

### STEP 7 — Vercel 환경변수 추가 ⚠️ 6개 전부

1. Vercel → 프로젝트 → **Settings → Environment Variables**
2. 아래 6개 추가

| Key | Value |
|---|---|
| `NOTION_TOKEN` | 시크릿 키 |
| `NOTION_DB_ID` | DB ID |
| `PROP_TITLE` | DB 제목 속성 이름 |
| `PROP_DATE` | DB 날짜 속성 이름 |
| `PROP_TYPE` | DB 유형 속성 이름 |
| `PROP_STATUS` | DB 상태 속성 이름 |

---

### STEP 8 — Redeploy ⚠️ 반드시

1. Vercel → **Deployments** 탭
2. 최근 배포 옆 **···** → **Redeploy** ✓

---

### STEP 9 — 노션에 임베드

1. 노션 페이지에서 `/embed` 입력
2. 배포 URL 붙여넣기

```
https://bluelady-calendar-xxx.vercel.app
```

> ⚠️ `https://` 반드시 포함

3. **임베드 링크** 클릭 ✓

---

## 문제 해결

브라우저에서 `https://본인배포URL/api/events` 직접 접속해보세요.

| 결과 | 해결 방법 |
|---|---|
| `{"events":[...]}` | 정상 — 임베드 URL 다시 확인 |
| `NOTION_TOKEN 없음` | 환경변수 확인 후 Redeploy |
| `page, not a database` | DB ID 다시 확인 (STEP 5) |
| 노션에서 연결 거부 | `https://` 포함 여부 확인 |

---

## 라이선스

재수정 및 재배포는 불가합니다.
