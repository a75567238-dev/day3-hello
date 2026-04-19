# Design System Strategy: Structural Clarity & Tonal Depth

## 1. Overview & Creative North Star: "The Digital Architect"
이 디자인 시스템의 핵심은 단순히 정보를 나열하는 것이 아니라, **'건축적 정교함(Structural Precision)'**과 **'공감각적 투명성(Ethereal Clarity)'**을 통해 브랜드의 신뢰를 구축하는 데 있습니다. 우리는 흔한 기업용 템플릿의 경직된 그리드를 탈피하고, 의도적인 비대칭과 여백의 미학을 활용하여 전문적이면서도 혁신적인 '디지털 큐레이터'로서의 정체성을 시각화합니다. 

이 시스템은 사용자에게 "정돈된 정보의 바다"를 항해하는 듯한 경험을 선사하며, 고대비의 타이포그래피 스케일과 섬세한 레이어링을 통해 고부가가치 기업의 권위를 표현합니다.

---

## 2. Color Strategy: The Blue & Surface Philosophy
신뢰를 상징하는 Blue와 깨끗한 White를 바탕으로 하되, 단순한 색 배합을 넘어선 **'톤의 위계(Tonal Hierarchy)'**를 구축합니다.

### The "No-Line" Rule
이 디자인 시스템에서는 섹션을 구분하기 위해 **1px의 실선(Solid Border) 사용을 엄격히 금지합니다.** 경계는 선이 아닌 면의 변화로 정의합니다.
*   **Surface Shifting:** `surface` 배경 위에 `surface-container-low` 섹션을 배치하거나, `surface-container-high` 요소를 얹어 시각적 경계를 만듭니다.
*   **Tonal Transition:** 면과 면이 만나는 지점에서 발생하는 미세한 명도 차이가 곧 가이드라인이 됩니다.

### Surface Hierarchy & Nesting
UI를 평면적인 종이가 아닌, 겹겹이 쌓인 **'반투명한 유리의 층'**으로 취급합니다.
*   **Base:** `surface` (#f7f9fb)
*   **Sectioning:** `surface-container-low` (#f2f4f6)
*   **Content Cards:** `surface-container-lowest` (#ffffff)를 사용하여 가장 밝게 띄워 가독성을 극대화합니다.

### The "Glass & Gradient" Rule
기성 제품의 느낌을 지우기 위해 메인 CTA와 히어로 섹션에는 `primary` (#003d9b)에서 `primary_container` (#0052cc)로 이어지는 **Signature Gradient**를 적용합니다. 또한, 플로팅 요소에는 `surface` 컬러에 80% 투명도와 20px 이상의 Backdrop-blur를 적용한 **Glassmorphism**을 적극 권장합니다.

---

## 3. Typography: Editorial Authority
가독성이 뛰어난 한글 타이포그래피를 위해 현대적인 **Manrope**(영문/숫자)와 **Inter**(국문 최적화 대응)를 조합합니다.

*   **Display & Headline (Manrope):** 혁신성을 상징하는 기하학적 서체입니다. `display-lg` (3.5rem)와 `headline-md` (1.75rem)를 과감하게 사용하여 핵심 메시지에 압도적인 권위를 부여합니다.
*   **Body & Label (Inter):** 전문적인 신뢰감을 위해 본문에는 높은 판독성을 가진 서체를 사용합니다. 한글 적용 시 행간(Line-height)은 본문 기준 1.6~1.7배를 유지하여 시각적 피로도를 낮춥니다.
*   **The Scale Logic:** 타이틀과 본문 사이의 크기 차이를 명확히 하여(Contrast), 사용자가 훑어보기(Scanning)만으로도 정보의 구조를 파악할 수 있도록 합니다.

---

## 4. Elevation & Depth: Tonal Layering
그림자(Shadow) 대신 **'톤의 적층'**을 통해 깊이감을 구현합니다.

*   **The Layering Principle:** 물리적인 두께감을 위해 `surface-container` 티어를 활용합니다. 가장 중요한 정보는 `surface-container-lowest` (#ffffff) 카드에 담아 시각적으로 가장 가깝게 느껴지도록 설계합니다.
*   **Ambient Shadows:** 부유하는 느낌이 반드시 필요할 경우, 그림자는 절대 검은색을 사용하지 않습니다. `on-surface` 컬러를 4%~8% 농도로 희석하고 Blur 값을 40px 이상으로 넓게 퍼뜨려, 자연광 아래의 은은한 그림자를 재현합니다.
*   **The "Ghost Border" Fallback:** 접근성 등을 위해 경계가 필수적인 경우, `outline-variant` (#c3c6d6) 토큰을 15% 투명도로 적용한 '고스트 보더'만을 허용합니다.

---

## 5. Signature Components

### Buttons: High-End Action
*   **Primary:** `primary` 그라데이션 배경 + `on_primary` 텍스트. `xl` (0.75rem) 또는 `full` 라운딩을 적용하여 혁신적이고 부드러운 인상을 줍니다.
*   **Secondary:** 배경색 없이 `primary` 텍스트와 `outline` 고스트 보더만 사용합니다.

### Input Fields: Clean Slate
*   전통적인 박스 형태를 지양합니다. `surface-container-highest` (#e0e3e5) 배경에 하단 2px의 `primary` 라인만 강조하거나, 전체적으로 아주 연한 `surface-variant` 톤을 채워 넣습니다. 테두리는 생략합니다.

### Cards & Lists: Pure Space
*   **No Dividers:** 리스트 아이템 사이의 구분선(Divider)을 삭제합니다. 대신 `spacing` 스케일을 활용한 충분한 수직 여백과, 마우스 오버 시 `surface-container-high`로 배경이 변하는 인터랙션으로 구분합니다.

### Signature Component: The Glass Breadcrumb
*   페이지 상단 내비게이션에는 Glassmorphism이 적용된 플로팅 바를 사용하여, 스크롤 시 배경 콘텐츠가 은은하게 비치도록 함으로써 전체적인 공간의 연결성을 강조합니다.

---

## 6. Do's and Don'ts

### ✅ Do
*   섹션 간 이동 시 과감한 **수직 여백(80px~160px)**을 사용하여 여유로운 프리미엄 무드를 조성하세요.
*   모든 코너 라운딩은 시스템의 `xl` (0.75rem) 값을 기본으로 하여 일관된 부드러움을 유지하세요.
*   핵심 수치나 데이터는 `display-md` 스케일을 사용하여 시각적 임팩트를 주어 전문성을 강조하세요.

### ❌ Don't
*   **절대 100% 불투명한 진한 회색 테두리를 사용하지 마세요.** 이는 디자인을 값싸고 딱딱하게 만듭니다.
*   한 화면에 너무 많은 Blue를 남발하지 마세요. Blue는 `primary` 포인트로서 존재할 때 가장 신뢰감이 높습니다. 나머지는 White와 Off-white(Surface)의 영역으로 남겨두세요.
*   그림자(Shadow)에 짙은 색상을 사용하지 마세요. 이는 '혁신성'을 저해하는 요소입니다.