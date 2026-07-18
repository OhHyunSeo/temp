# Gemini Learning Notes

- **날짜**: 2026-07-18
- **내용**: 기존에 `localStorage`를 사용하여 저장/불러오기를 처리하던 바닐라 자바스크립트 프로젝트를 **Supabase**를 활용하여 데이터베이스 연동 방식으로 마이그레이션함.
- **Supabase 연동 방식**: 
  - 빌드 과정 없이 GitHub Pages에 바로 배포하기 위해 Supabase의 JS CDN( `@supabase/supabase-js` )을 `<script>` 태그로 로드하여 사용.
  - `YOUR_SUPABASE_URL` 과 `YOUR_SUPABASE_ANON_KEY`를 사용해 클라이언트를 초기화함.
  - `fetchSchedules` (조회), `submitDate` (등록) 함수에서 async/await 문법을 활용하여 Supabase API 통신 처리.
- **Supabase 테이블 생성(DDL)**:
  - `travel_schedules` 테이블 생성 (`id`, `name`, `start_date`, `end_date`, `created_at`).
  - GitHub Pages처럼 프론트엔드 단독 환경일 때는 인증 절차가 따로 없으므로 RLS(Row Level Security)를 활성화한 상태에서, `SELECT` 와 `INSERT` 권한을 모두에게 개방(`USING (true)`)하는 정책(Policy) 추가 필요.
