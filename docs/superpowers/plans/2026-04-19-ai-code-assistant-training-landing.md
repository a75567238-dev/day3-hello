# AI 코드 어시스턴트 교육 랜딩페이지 구현 계획

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 40대 이상 성인 대상의 신뢰형 정적 한 페이지 랜딩을 구현해 카카오톡 상담 전환을 유도한다.

**Architecture:** 단일 `index.html`에 의미 기반 섹션(히어로/효과/진행 방식/신뢰 근거/FAQ/CTA)을 순서대로 배치한다. 모든 CTA는 동일한 카카오톡 링크로 통일하고, 모바일 우선 레이아웃과 고정 하단 CTA로 전환 접근성을 확보한다. JavaScript는 최소화하고 앵커 스크롤 및 링크 실패 대체 안내는 HTML 구조와 간단한 속성 설계로 처리한다.

**Tech Stack:** HTML5, CSS3(내장 스타일), 바닐라 JavaScript(최소)

---

## 파일 구조 및 책임
- Modify: `index.html`
  - 페이지 전체 구조(섹션 IA), 카피, CTA 링크, FAQ, 반응형 스타일, 모바일 고정 CTA를 단일 파일에서 관리
- Reference: `docs/superpowers/specs/2026-04-19-ai-code-assistant-training-landing-design.md`
  - 구현 기준(요구사항/범위/검증 기준)

---

### Task 1: 기본 레이아웃과 히어로/CTA 골격 구현

**Files:**
- Modify: `index.html`
- Test: `index.html` 브라우저 수동 확인

- [ ] **Step 1: 히어로 중심의 실패 기준 체크리스트 작성**

```text
체크리스트(초기 상태에서는 실패 예상):
1) 메인 카피가 "비개발자도 이해하는 실전 AI 코드 어시스턴트"인지
2) 상단 CTA 버튼 문구가 "카카오톡으로 상담받기"인지
3) 헤더/히어로/기본 섹션 컨테이너가 존재하는지
```

- [ ] **Step 2: 현재 페이지가 체크리스트를 만족하지 못함을 확인**

Run: 브라우저에서 `index.html` 열기
Expected: 현재 "hello world 1"만 있어 3개 항목 모두 실패

- [ ] **Step 3: 최소 구현으로 헤더/히어로/기본 CTA 구조 작성**

```html
<!doctype html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AI 코드 어시스턴트 교육 프로그램</title>
  </head>
  <body>
    <header>
      <div>AI 코드 어시스턴트 교육</div>
      <a href="#cta">카카오톡으로 상담받기</a>
    </header>

    <main>
      <section id="hero">
        <h1>비개발자도 이해하는 실전 AI 코드 어시스턴트</h1>
        <p>40대 학습자도 이해하기 쉬운 실습 중심 교육</p>
        <a href="#cta">카카오톡으로 상담받기</a>
      </section>

      <section id="cta">
        <h2>지금 상담으로 시작하세요</h2>
        <a href="https://open.kakao.com/" target="_blank" rel="noopener noreferrer">카카오톡으로 상담받기</a>
      </section>
    </main>
  </body>
</html>
```

- [ ] **Step 4: 체크리스트 재검증**

Run: 브라우저에서 새로고침 후 텍스트/버튼 확인
Expected: 3개 항목 모두 PASS

- [ ] **Step 5: 커밋**

```bash
git add index.html
git commit -m "feat: add landing hero and primary CTA skeleton"
```

---

### Task 2: 정보구조 전체 섹션(효과/진행/신뢰/FAQ/하단 CTA) 구현

**Files:**
- Modify: `index.html`
- Test: `index.html` 브라우저 수동 확인

- [ ] **Step 1: 실패 기준 체크리스트 작성(섹션 존재 여부)**

```text
체크리스트(초기 상태에서는 실패 예상):
1) 프로그램 효과 3포인트 섹션 존재
2) 진행 방식 3단계 섹션 존재
3) 신뢰 근거 섹션 존재
4) FAQ 4문항 존재
5) 하단 CTA 섹션 존재
```

- [ ] **Step 2: 현재 상태에서 실패 확인**

Run: 브라우저에서 `index.html` 확인
Expected: Task 1 기준 최소 구조라 위 항목 다수 FAIL

- [ ] **Step 3: 스펙 기준 섹션 콘텐츠 최소 구현**

```html
<section id="benefits">
  <h2>프로그램 효과</h2>
  <ul>
    <li>반복 작업 시간 단축</li>
    <li>실무에 바로 적용 가능한 학습</li>
    <li>어려운 개념을 쉬운 언어로 이해</li>
  </ul>
</section>

<section id="process">
  <h2>진행 방식</h2>
  <ol>
    <li>카카오톡 상담 신청</li>
    <li>현재 수준 진단 및 과정 안내</li>
    <li>수강 시작 및 적용 피드백</li>
  </ol>
</section>

<section id="trust">
  <h2>신뢰 근거</h2>
  <ul>
    <li>실무 경험 기반 강의</li>
    <li>질문 응답 중심 운영</li>
    <li>수강 후기 요약 제공</li>
  </ul>
</section>

<section id="faq">
  <h2>자주 묻는 질문</h2>
  <details><summary>비개발자인데 가능한가요?</summary><p>기초부터 단계별로 안내합니다.</p></details>
  <details><summary>어느 정도 시간이 필요한가요?</summary><p>개인 일정에 맞춰 상담 시 안내합니다.</p></details>
  <details><summary>준비물은 무엇인가요?</summary><p>기본 PC와 인터넷 환경이면 시작 가능합니다.</p></details>
  <details><summary>수강 전 상담이 가능한가요?</summary><p>카카오톡으로 사전 상담이 가능합니다.</p></details>
</section>

<section id="final-cta">
  <h2>지금 수준에서 시작 가능한 맞춤 안내</h2>
  <a href="https://open.kakao.com/" target="_blank" rel="noopener noreferrer">카카오톡으로 상담받기</a>
</section>
```

- [ ] **Step 4: 체크리스트 재검증**

Run: 브라우저 새로고침 후 섹션 순서 확인
Expected: 5개 항목 모두 PASS

- [ ] **Step 5: 커밋**

```bash
git add index.html
git commit -m "feat: add core conversion sections for one-page landing"
```

---

### Task 3: 신뢰형 비주얼/반응형/가독성 스타일 적용

**Files:**
- Modify: `index.html`
- Test: 브라우저 DevTools 반응형 뷰

- [ ] **Step 1: 스타일 실패 기준 작성**

```text
체크리스트(초기 상태에서는 실패 예상):
1) 차분한 색상 대비와 충분한 여백 적용
2) 본문/제목 가독성(폰트 크기, 줄간격) 확보
3) 모바일(약 390px)에서 레이아웃 깨짐 없음
```

- [ ] **Step 2: 현재 상태 실패 확인**

Run: DevTools 모바일 뷰에서 확인
Expected: 기본 브라우저 스타일이라 1,2 실패 가능성 높음

- [ ] **Step 3: 내장 CSS로 신뢰형 스타일 최소 구현**

```html
<style>
  :root {
    --bg: #f7f8fb;
    --surface: #ffffff;
    --text: #1f2937;
    --muted: #4b5563;
    --primary: #1d4ed8;
    --primary-strong: #1e40af;
    --border: #e5e7eb;
  }

  * { box-sizing: border-box; }
  body {
    margin: 0;
    font-family: "Noto Sans KR", "Malgun Gothic", sans-serif;
    color: var(--text);
    background: var(--bg);
    line-height: 1.6;
  }

  .container {
    width: min(960px, 92%);
    margin: 0 auto;
  }

  section {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 32px 24px;
    margin: 16px 0;
  }

  h1 { font-size: clamp(1.8rem, 4vw, 2.4rem); line-height: 1.3; }
  h2 { font-size: clamp(1.3rem, 3vw, 1.7rem); margin-top: 0; }
  p, li, summary { color: var(--muted); }

  .btn {
    display: inline-block;
    background: var(--primary);
    color: #fff;
    text-decoration: none;
    padding: 12px 18px;
    border-radius: 10px;
    font-weight: 700;
  }

  .btn:hover { background: var(--primary-strong); }

  @media (max-width: 640px) {
    section { padding: 24px 16px; }
  }
</style>
```

- [ ] **Step 4: 반응형/가독성 재검증**

Run: 데스크톱 + 모바일(390px)에서 시각 확인
Expected: 1~3 항목 모두 PASS

- [ ] **Step 5: 커밋**

```bash
git add index.html
git commit -m "style: apply trust-focused visual system and responsive typography"
```

---

### Task 4: CTA 통일, 모바일 고정 CTA, 링크 실패 대체 안내 구현

**Files:**
- Modify: `index.html`
- Test: 브라우저 클릭 테스트

- [ ] **Step 1: 실패 기준 체크리스트 작성**

```text
체크리스트(초기 상태에서는 실패 예상):
1) 히어로/중간/하단 CTA가 동일 링크 사용
2) 모바일 하단 고정 CTA 표시
3) 링크 실패 대비 대체 연락 수단 텍스트 노출
```

- [ ] **Step 2: 현재 상태 실패 확인**

Run: 모든 CTA href 값을 확인
Expected: 통일/고정 CTA/대체 안내 중 일부 FAIL

- [ ] **Step 3: CTA 링크 상수화 및 고정 버튼/대체 안내 추가**

```html
<script>
  const KAKAO_URL = "https://open.kakao.com/o/example";
  document.querySelectorAll('[data-role="kakao-cta"]').forEach((el) => {
    el.setAttribute("href", KAKAO_URL);
  });
</script>

<!-- 하단 고정 CTA -->
<div class="sticky-cta">
  <a class="btn" data-role="kakao-cta" target="_blank" rel="noopener noreferrer">카카오톡으로 상담받기</a>
</div>

<!-- 대체 연락 안내 -->
<p class="fallback-contact">카카오톡 연결이 원활하지 않다면 010-1234-5678 또는 sample@example.com 으로 연락해주세요.</p>
```

```html
<style>
  .sticky-cta {
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    padding: 10px 16px;
    background: rgba(255, 255, 255, 0.96);
    border-top: 1px solid var(--border);
    display: none;
  }

  .sticky-cta .btn {
    width: 100%;
    text-align: center;
  }

  .fallback-contact {
    font-size: 0.95rem;
    color: var(--muted);
  }

  @media (max-width: 640px) {
    .sticky-cta { display: block; }
    body { padding-bottom: 74px; }
  }
</style>
```

- [ ] **Step 4: 행동 흐름 검증**

Run: 페이지 내 모든 CTA 클릭 및 href 검사
Expected: 모든 CTA가 동일 `KAKAO_URL`로 이동, 모바일에서 고정 CTA 노출, 대체 연락 안내 텍스트 확인

- [ ] **Step 5: 커밋**

```bash
git add index.html
git commit -m "feat: unify kakao CTAs with mobile sticky action and fallback contact"
```

---

### Task 5: 최종 검증 및 정리

**Files:**
- Modify: `index.html` (필요 시 미세 수정)
- Test: 브라우저 최종 점검

- [ ] **Step 1: 스펙 기반 최종 검증 체크리스트 작성**

```text
1) 섹션 순서: 히어로 → 효과 → 진행 방식 → 신뢰 근거 → FAQ → 하단 CTA
2) 핵심 문구: "비개발자도 이해하는 실전 AI 코드 어시스턴트"
3) CTA 문구: "카카오톡으로 상담받기"
4) CTA 링크 통일 + 모바일 고정 CTA
5) 링크 실패 대체 연락 문구 존재
6) 반응형 레이아웃 정상
```

- [ ] **Step 2: 브라우저 수동 테스트 실행**

Run:
- 데스크톱 브라우저에서 `index.html` 전체 스크롤 점검
- 모바일 뷰(390x844)에서 전체 스크롤/CTA 점검

Expected: 1~6 항목 모두 PASS

- [ ] **Step 3: 필요 시 최소 수정 반영**

```html
<!-- 예시: 텍스트/간격 조정은 index.html 내 해당 요소에서 직접 수정 -->
```

- [ ] **Step 4: 최종 커밋**

```bash
git add index.html
git commit -m "chore: finalize one-page landing QA and polish"
```

- [ ] **Step 5: 완료 보고 준비**

```text
보고 항목:
- 구현된 섹션 목록
- CTA 흐름 구현 요약
- 테스트 결과(데스크톱/모바일)
- 확장 가능 포인트(다중 페이지, 실제 카카오 채널 URL 교체)
```

---

## Self-Review 결과

### 1) Spec coverage 점검
- 목표/타깃/톤: Task 1~3에서 반영
- IA(히어로~하단 CTA): Task 2에서 반영
- 행동/데이터 흐름(CTA 통일): Task 4 반영
- 예외 처리(대체 연락 수단): Task 4 반영
- 검증 기준(반응형/CTA/가독성): Task 3, Task 5 반영
- 제외 범위(결제/백엔드/다중 페이지): 계획 전체에서 미포함 유지

### 2) Placeholder scan
- 금지 플레이스홀더 표현 없음
- 모호 지시 표현 없음

### 3) Type/명칭 일관성
- CTA 문구/핵심 카피/섹션 명칭 일관 유지
- 카카오 링크는 `KAKAO_URL`로 단일 명칭 유지
