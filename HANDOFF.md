# Handoff: Intent Engineering 사이트

## 현재 상태

GH Pages 사이트의 초안이 완성됨. 로컬에서 `docs/index.html`을 브라우저로 열면 확인 가능. 아직 GitHub에 push하지 않은 상태.

## 파일 구조

```
intent-engineering/
├── .gitignore
├── LICENSE                     # MIT
├── README.md                   # 프로젝트 소개
├── INTENT.template.md          # 사용자가 복사해서 쓸 템플릿
├── HANDOFF.md                  # 이 문서
└── docs/                       # GH Pages 서빙 폴더
    ├── .nojekyll               # Jekyll 비활성화
    ├── index.html              # 랜딩 페이지
    └── guide/
        ├── quickstart.html     # 5분 퀵스타트 가이드
        └── concept.html        # 패러다임 전체 개념 설명
```

## 배포 방법

```bash
# 1. GitHub 레포 생성 (roboco-io/intent-engineering)
gh repo create roboco-io/intent-engineering --public --source=. --remote=origin

# 2. 첫 커밋 및 push
git add -A
git commit -m "Initial commit: Intent Engineering paradigm site"
git push -u origin main

# 3. GH Pages 활성화 (Settings → Pages → Source: main branch, /docs folder)
# 또는 CLI로:
gh api repos/roboco-io/intent-engineering/pages -X POST -f source.branch=main -f source.path=/docs
```

배포 URL: `https://roboco-io.github.io/intent-engineering/`

## 사이트 구성

### 랜딩 (index.html)
- Hero: "Ship intent, not code."
- 섹션 01 — The Problem: 스킬 없이 337줄 vs 스킬 적용 47줄 비교
- 섹션 02 — The Framework: Why/What/Not/Learnings 네 레이어
- 섹션 03 — The Lifecycle: seed → exploring → clarified → killed
- 섹션 04 — The Pipeline: 사람이 개입하는 두 지점 (의도 작성, 학습/판단)
- 섹션 05 — Principles: Never write How, Admit uncertainty, Kill fast, Intent precision = output quality

### Quick Start (guide/quickstart.html)
- 5단계: 상태 선택 → INTENT.md 생성 → 탐구/학습 → 상태 전이 → AI 핸드오프
- seed/exploring용 템플릿과 clarified용 템플릿 모두 포함

### Concept (guide/concept.html)
- 패러다임의 배경과 근거
- 기존 개념(Context Engineering, Harness Engineering, Spec-driven, Vibe Coding)과의 관계
- 자동화 파이프라인 도해
- 왜 작동하는지에 대한 논거

## 디자인 결정 사항

- **순수 HTML/CSS, 빌드 도구 없음.** 의도적 선택. Intent Engineering의 철학(최소한만, 불필요한 것 제거)에 부합
- **다크 테마.** 개발자 타겟
- **영문.** 글로벌 대상. 한국어 버전은 추후 필요 시 `docs/ko/` 하위에 추가
- **모바일 반응형.** CSS Grid + clamp 사용

## 다음 단계 (우선순위 순)

### 즉시
- [ ] GitHub 레포 생성 및 push
- [ ] GH Pages 활성화
- [ ] 브라우저에서 배포 URL 확인

### 개선
- [ ] 랜딩 페이지 실제 브라우저 테스트 후 레이아웃 미세 조정
- [ ] OG 메타 태그 추가 (소셜 공유용 title, description, image)
- [ ] favicon 추가
- [ ] 337줄 vs 47줄 비교 데이터는 실제 테스트 결과에서 나온 것 — 필요 시 이미지나 스크린샷으로 증거 추가

### 확장
- [ ] 한국어 버전 (`docs/ko/`)
- [ ] 실제 사례 페이지 (`docs/guide/examples.html`) — 실 프로젝트의 INTENT.md 예시
- [ ] Intent Engineering 스킬 배포 연동 — 스킬 .skill 파일 다운로드 링크
- [ ] 블로그 포스트 또는 소셜 공유용 축약 버전

## 관련 자산

### Intent Engineering 스킬
`/Users/dohyunjung/Workspace/roboco-io/tools/plugins/plugins/workflow/skills/intent-engineering/`에 위치. SKILL.md + 5개 템플릿 (why-explore, why-commit, what, not, learning). 생명주기(seed/exploring/clarified/killed) 포함.

### 오늘 만든 파일들 (지출증빙 폴더)
- `INTENT.template.md` — 독립 템플릿
- `intent-engineering-concept.md` — 한국어 개념 문서 초안
- `intent-engineering.skill` — 패키징된 스킬 파일
- `intent-engineering-eval-review.html` — 테스트 비교 결과 (with/without skill)

## 핵심 컨텍스트

이 패러다임의 핵심 주장:

1. **바이브 코딩 시대에 코드는 병목이 아니다. 의도의 부재가 병목이다.**
2. **Spec 작성, 하네스 엔지니어링, 컨텍스트 엔지니어링은 모두 자동화 가능하다. 자동화할 수 없는 것은 Why/What/Not에 대한 인간의 결정뿐이다.**
3. **의도는 한 번 적는 것이 아니라, 탐구와 학습을 통해 수렴하는 것이다. 수렴이 안 되면 종료(kill)하는 것도 좋은 결과다.**
4. **사람이 개입하는 지점은 파이프라인의 맨 위(의도 작성)와 맨 아래(학습/판단) 두 곳뿐이다.**

이 문서를 읽은 뒤 삭제해도 됩니다.
