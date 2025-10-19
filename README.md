# 정진영 포트폴리오 사이트 | wlsdudwjd.github.io

> 전북대학교 컴퓨터인공지능학부 정진영의 개인 포트폴리오 사이트입니다! 한국어와 영어를 모두 지원하며, 학습 기록과 프로젝트, 경력 소개를 보기 쉽게 정리했습니다.

## 🧭 사이트 안내
- `소개, Introduction` – 풀스크린 슬라이더와 함께 자기소개, 현재 학습 중인 주제, 주요 프로젝트를 카드로 보여줍니다.
- `학습, Studying` – Java, Spring, MR 등 학습 노트를 모아둔 컬렉션 페이지입니다.
- `경력, Experience` – 학생회와 동아리 활동을 연도별로 정리했습니다.
- `프로젝트, Projects` – 전화번호부 앱, Pacman, Linux 프로젝트 등 결과물을 상세 설명과 링크로 제공합니다.
- `연락, Contact` – 이메일·소셜 링크와 함께 전북대학교 7호관 위치 지도를 제공합니다.
- 모든 페이지는 `content/ko/...`와 `content/en/...`에 동일한 경로로 존재해 다국어 전환이 간단합니다.

## ✨ 특징
- **다국어 지원**: `config/_default/languages.yaml`과 `menus.{ko,en}.yaml`에서 언어별 메뉴와 기본 언어를 설정합니다.
- **맞춤형 히어로 슬라이더**: `layouts/partials/{en_,}slider.html`이 Swiper.js로 전체 화면 이미지를 전환하며 소개 문구를 출력합니다.
- **학습/프로젝트 카드**: `content/{lang}/studying`, `projects`에서 `featured: true`로 표시한 글이 메인 화면 카드에 노출됩니다.
- **이력서 다운로드**: 메인 소개 섹션의 버튼이 `static/main/uploads/resume.pdf`와 바로 연결됩니다.
- **전체 검색**: Pagefind가 정적 검색 인덱스를 생성해 모든 페이지에서 바로 검색할 수 있습니다.

## 📂 주요 폴더

| 경로 | 설명 |
| --- | --- |
| `content/ko`, `content/en` | 페이지 콘텐츠. 같은 경로의 KO/EN 파일을 함께 수정합니다. |
| `content/{lang}/authors/admin/_index.md` | 프로필, 학력, 수상, 스킬 정보를 정의합니다. |
| `content/{lang}/main/_index.md` | 메인 페이지 섹션(소개, 학습, 프로젝트) 구성 |
| `layouts/partials/{en_,}slider.html` | 슬라이더 이미지·문구 설정 |
| `layouts/shortcodes/{en_,}slider.html` | 슬라이더 숏코드 (`{{< slider >}}`) |
| `assets/css/custom.css` | 네비게이션 hover, 다크 모드 대비, 본문 정렬 등 커스텀 스타일 |
| `static/media/` | 슬라이더 배경 이미지 (`image1~3.jpg`) |
| `static/main/uploads/` | 이력서 PDF 등 다운로드 자료 |
| `.github/workflows/deploy.yml` | GitHub Pages 자동 배포 파이프라인 |
| `netlify.toml` | Netlify 빌드 명령과 환경 변수 |
