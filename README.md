# 줍(Zoop) 프로젝트 정리 — LG CNS 5기 AM INSPIRE CAMP 2조 금융

> LG CNS 5기 AM INSPIRE CAMP 2조 금융 프로젝트(줍/Zoop)의 전체 작업과 박주형의 프론트엔드 담당 작업을 정리한 개인 기록이다.
> 기준일: 2026-11-10 (GitHub 조회 기준). 커밋 수에는 머지 커밋이 포함된다. 실명 매핑은 GitHub 로그인만으로 확정하지 않았다.
> 개인 Notion 정리본: https://app.notion.com/p/41404baf6e058148942dc43172611f29

## 1. 프로젝트 개요

- **프로젝트:** 줍(Zoop) — 뉴스·공시 기반 기업 관계 탐색 서비스, 금융 사건 관계 지도
- **과정:** LG CNS 5기 AM INSPIRE CAMP, 2조 금융
- **팀명:** 돈벌래
- **멘토:** 정상덕
- **팀장:** 김도현
- **멘티:** 박주형, 임현, 윤서진, 김도현, 홍정현, 안재현, 정세빈
- **클라우드 담당:** 안재현
- **프론트엔드(FE):** 박주형, 김도현
- **백엔드(BE):** 윤서진, 임현, 정세빈, 홍정현
- **조직:** https://github.com/Donbug
- **레포 2개**
  - [Donbug/zoop](https://github.com/Donbug/zoop) — 본개발. 2026-10-01 생성, 2026-11-09 최근 활동
  - [Donbug/Zoop-Infra](https://github.com/Donbug/Zoop-Infra) — AWS 인프라, Docker 통합환경, CI/CD. 2026-10-06 생성, 2026-11-09 최근 활동
- **원본 팀 노션:** https://app.notion.com/p/2-3cafef49d8d580cb9a25e53f97ec3f90
- **Figma 최종:** https://www.figma.com/design/B1nkTuCLKWMohgXNdEB6un/돈벌래-최종-프로젝트
- **WBS:** https://docs.google.com/spreadsheets/d/1aHJbxjXmvzgTXAlBd4mWTRDkcvD1S9vtHl1PR_bxn5c/edit?gid=136329476#gid=136329476

## 2. 전체 구조와 스택

### zoop
- 최상위: `web/`, `api/`, `ai/`, `prototype/`, `docs/`, `data/`, `demo/`, `deployment/`, `scripts/`, `tools/`
- **프론트엔드 본개발 `web/`:** React 19.2.8 + Vite 8 + TypeScript + Tailwind CSS 4, pnpm, Zustand 5, axios, react-router-dom 7, Vitest + Testing Library
- **그래프:** AntV G6 5.1.1 (`web/src/components/graph/`, `GraphCanvas.tsx`, `graph-appearance.ts`, `graph-model.ts` 등)
- **프로토타입 `prototype/web`:** Cytoscape 3.34.3 기반 — 본개발과 구분됨
- **백엔드 `api/`:** Java 21 / Spring Boot (Gradle), PostgreSQL + 합성 스냅샷, Neo4j는 스냅샷 경유
- **AI `ai/`:** worker / pipeline / service 3개 프로젝트
- **문서 `docs/`:** OpenAPI 정본(84개 operation), design, evidence, screen-plan, system(WBS 추적), specs, wireframe 등
- 부속 파일: `줍_프로젝트_WBS_2026-09-29_11-06.xlsx`, `줍_요구사항명세서_v0.2.docx` (바이너리라 이번 조회에서 내용 미확인)

### Zoop-Infra
- `terraform/`, `first47-staging/`, `docs/`, `scripts/`, `.github/`
- AWS ECS/Fargate, Neo4j EC2, RDS PostgreSQL, ElastiCache Valkey, CloudFront, ALB, ECR, S3 원격 state

## 3. 전체 활동량 (2026-11-10 조회)

### zoop — 커밋 1,802개 (2026-10-01 → 2026-11-09), PR 448개(머지 421개), 이슈 156개(closed 110개, open 46개)

| 작성자 | 커밋 | 비중 | 주 스코프 |
|---|---|---|---|
| KIM-korea | 564 | 31.3% | api, ai, docs, contracts, merge-pr 138 |
| sebinJeong | 391 | 21.7% | api 213 |
| jhh6079 | 250 | 13.9% | api 83, briefing 63 |
| david3123123 (박주형) | 249 | 13.8% | web 208 |
| limhyun0319 | 175 | 9.7% | api 59, web 30 |
| SJY051 | 122 | 6.8% | ai 53, api 26 |
| GgaGGa0302 | 51 | 2.8% | ai/chat/ci 등 |

### Zoop-Infra — 커밋 87개, PR 54개(전부 머지), 이슈 22개(closed 21개, open 1개)
- GgaGGa0302: 커밋 86개, PR 53개 — 사실상 단독 담당
- SJY051: 커밋 1개, PR 1개
- open 이슈 1개: #59 [Infra] Dev Terraform 배포 상태 드리프트 정리 (담당 GgaGGa0302)

## 4. 타임라인 (검증된 날짜만)

- 2026-10-01: zoop 생성, 첫 커밋(SJY051)
- 2026-10-06: Zoop-Infra 생성·첫 커밋(GgaGGa0302)
- 2026-10-12: 박주형 첫 커밋·PR(#2 LF 고정, #4 Vitest·Testing Library 환경). WBS 기능 이슈 대량 생성
- 2026-10-12~14: WBS 이슈 생성 러시, 인증·온보딩·기업 상세 구현 PR 시작
- 2026-10-14: Infra Terraform 구축 집중일(PR #5~#29)
- 2026-10-17: #214 박주형 자가 발행·당일 해결
- 2026-11-02~05: 박주형 지도/그래프 집중 수정 기간(PR #504~#590)
- 2026-11-09: 양 레포 최근 활동 — zoop #601/#602(박주형), Infra #75(SJY051)·#76(GgaGGa0302)

## 5. 박주형(david3123123) 담당 — 프론트엔드 전담

### 규모
- 커밋 249개(2026-10-12~11-09): web 208개, merge-pr 23개, merge-branch 12개, api 3개, contracts 1개, infra(CI) 1개
  - git identity 2개 합산: `박주형 <298907699+david3123123@users.noreply.github.com>` 160건 + `david3123123 <david3123123@gmail.com>` 89건
- PR 137개 중 135개 머지, 미머지 종료 2개(#512, #369), open 0개 — 팀 최다
- 담당 이슈 31개(closed 24개, open 7개), 직접 작성 이슈 11개(전부 closed)

### PR 주제별
- 지도/그래프 55개, 기업 상세 17개, 인증/온보딩 11개, 브리핑 6개, 내 종목/관심 6개, 관리자 4개, AI 채팅 3개, 기타 35개

### 담당 이슈 (WBS 기준)
- 6.2.x 인증: #34 D-AUT-01 로그인, #35 D-AUT-02 회원가입, #36 인증 통합 테스트, #199 비밀번호 검사(closed)
- 6.3.x 온보딩: #9 D-ONB-01, #10 D-ONB-02, #11 D-WAT-01b, #12 D-MY-01, #45 온보딩 통합 테스트(open)
- 6.4.x 내 종목/관심: #50 D-STK-01, #51 내 종목 통합 테스트
- 6.7.x 기업 상세: #91 D-COM-01·01b, #92 D-COM-02, #93 D-COM-03, #94 D-COM-04, #95 D-COM-05·06, #96 기업 상세·타임라인 통합 테스트(open)
- 6.8.x 브리핑: #107 D-BRF-01, #108 D-BRF-02, #109 D-BRF-04, #110 브리핑 그래프·개인화 UI, #111 출퇴근 브리핑 통합 테스트(open)
- 6.10.x 관리자: #139 A-ADM-05c, #140 A-ADM-01, #141 A-ADM-02·02b, #143 A-ADM-04·04b, #144 A-ADM-05·05b, #145 관리자 통합 테스트(open)
- 6.11.x 마무리: #146 API·스키마 계약 통합 점검(open), #152 결함 수정·회귀 테스트(open), #154 시연 영상·발표 PPT(open)
- open 7개는 전부 테스트·문서 계열. 기능 구현 이슈는 담당분 전원 closed.

### 대표 작업
- #214 (2026-10-17): D-GRP-01 노드 호버 시 관련 이슈·연결선 강조 누락 — 본인 발행·당일 해결. 호버 노드와 직접 연결 노드·연결선 강조, 무관 노드 불투명도 35%·연결선 20%, 마우스 떼면 복원.
- 최근 PR: #602(2026-11-09, 개발 목업 모드에서 관리자 이슈 후보를 지도 목업으로 채우기), #601(2026-11-09, AI 채팅 말풍선·마크다운 답변 정리)
- 기타 대표 PR: #590 ZOOP 로고 적용, #588 지도 빈 캔버스 드리프트 수정, #569 줌 %·이슈 노드 원형화, #550 동일 제목 사건 노드 통합, #538 first47 기업 로고, #529 기업 상세 종합, #517 AI 채팅 멀티 타겟, #510 기업 상세 시세·차트 정리, #507 로그인·가입 화면, #505 AI 채팅 작업 보기, #504 지도 사건·경로 패널
- 프론트 외 기여: #536 feat(api): 관리자 대화록 마스킹 조회와 열람 감사 기록, #164 ci(infra) 루트 web/을 CI app-web job으로 검사, #337 docs(contracts) getAiUsage 제안 필드

### 작업 방식 (코드 기준)
- 본개발 `web/` 기준, 프로토타입이 아닌 정식 프론트에서 작업
- 그래프는 AntV G6 기반 `GraphCanvas.tsx` 중심, 기업/사건/관계 상세 패널(`CompanyDetailPanel.tsx`, `EventDetailPanel.tsx`, `RelationDetailPanel.tsx`) 포함
- Figma v2.1 스펙 기준 화면 구현 (파일키 B1nkTuCLKWMohgXNdEB6un)

## 6. 실행 방법 (팀 노션 기준)

- api: `SPRING_PROFILES_ACTIVE=local ./gradlew bootRun`
- DB 띄우기: `docker compose --env-file api/.env -f api/compose.local.yaml up -d --wait`
- web: `pnpm dev`

## 7. 미확인 / 후속 확인 사항
- [ ] 팀 Notion 회의록·일정 하위 페이지 내용 (이번 조회에서 못 읽음)
- [ ] WBS 엑셀·요구사항명세서(docx) 내용 파싱
- [ ] 디자인 담당자 실명·범위 (GitHub 데이터만으로 특정 불가)
- [ ] README 언급 `Donbug/investmate-poc` 존재 여부 (조직 검색에 없음)
- [ ] 팀원 실명 ↔ GitHub 로그인 매핑 (사용자 확인 필요)
