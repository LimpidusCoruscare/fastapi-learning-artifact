# FastAPI 실습실

> **English summary** — A Korean-language study page that condenses the official FastAPI documentation (basics, intermediate, advanced) into 26 chapters and **runs real FastAPI inside the browser** with Pyodide. Nothing to install, no server needed. It includes an editable lab with request tracing, 20 auto-graded exercises and quizzes.
>
> - **Open:** <https://limpiduscoruscare.github.io/fastapi-learning-artifact/> (or serve the folder locally with `python -m http.server`)
> - **Progress:** stored in your browser's localStorage. Optionally, sync it to a private GitHub Gist or export/import it as a JSON file. Use the "동기화" button in the sidebar.
> - **Licenses:** based on the FastAPI documentation (MIT). Third-party copyright notices and license texts are in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

FastAPI 공식 문서(기초 · 중급 · 고급)를 26개 챕터로 정리하고, **브라우저 안에서 실제 FastAPI를 실행**해 보는 학습 페이지입니다. 설치할 것도, 서버도 필요 없습니다.

- **실습실:** 예제 코드를 고쳐 실행하고 요청을 보내 응답을 확인합니다 (Pyodide · Python 3.14 · FastAPI 0.146.0 · Pydantic 2.14.1)
- **요청 흐름:** 미들웨어 → 라우팅 → 의존성 → 검증 → 경로 함수 → 응답 단계, 요청마다 "왜 이 응답이 나왔나" 설명, 단계별 흐름과 편집기 줄 강조
- **편집기:** CodeMirror 6 + Jedi 자동완성(<kbd>Ctrl</kbd>+<kbd>Space</kbd>), 함수 시그니처, 문법 오류 표시
- **연습문제 20개 자동 채점** (빈칸 · 처음부터 · 버그 고치기 · 테스트 작성), 퀴즈, 진도
- **SQL 챕터:** SQLModel + 내장 SQLite, DB 들여다보기와 SQL 직접 실행

## 열기

GitHub Pages: <https://limpiduscoruscare.github.io/fastapi-learning-artifact/>

로컬에서 열 때는 파일을 더블클릭하지 말고 정적 서버로 띄우세요 (`fetch`가 `file://`에서는 막힙니다).

```bash
python -m http.server 8000
# http://localhost:8000
```

## 알아 둘 점

- 진도와 연습문제 초안은 기본적으로 **이 브라우저(localStorage)에** 저장됩니다.
- 다른 기기와 이어서 보려면 왼쪽 진도 카드의 **동기화**를 누르세요.
  - **Gist 동기화:** [Fine-grained 토큰](https://github.com/settings/personal-access-tokens/new)(Account permissions → Gists: Read and write)을 넣으면 내 계정에 비공개 Gist(`fastapi-lab-state.json`)를 만들어 자동으로 저장합니다. 다른 기기에서 같은 토큰을 넣으면 그 Gist를 찾아 합칩니다. 토큰은 그 브라우저에만 저장됩니다.
    - 진도 · 퀴즈 · 통과 기록은 바뀌고 3초 뒤 올립니다.
    - 연습문제 코드 초안은 GitHub API 사용량을 아끼려고 **처음 고친 뒤 5분 안에 한 번** 모아서 올리고, 탭을 벗어나거나 창을 닫을 때·"지금 동기화"를 누를 때는 바로 올립니다. 이 브라우저에는 0.5초마다 저장됩니다.
    - 탭으로 돌아오면 다른 기기의 변경을 받아 옵니다. 바뀐 게 없으면 GitHub이 304로 답해 사용량에 계산되지 않습니다.
  - **파일로 옮기기:** JSON으로 내보내고 다른 브라우저에서 가져오면 진도가 합쳐집니다.
- "실행 환경 켜기"를 누르면 약 15MB를 내려받습니다. Pyodide 엔진은 jsDelivr CDN에서, 표준 라이브러리와 패키지는 이 저장소의 `py/`에서 받습니다. SQL 챕터는 처음 열 때 SQLAlchemy · SQLModel(약 2.8MB)을 추가로 받습니다.
- WebSocket 챕터는 브라우저 실행 환경에서 지원되지 않아 코드를 로컬에서 실행해야 합니다.
- 기록된 응답은 로컬 CPython에서 같은 버전으로 실제 실행한 결과이고, 브라우저 실행 결과와 같은지 검증했습니다.

## 파일

| 경로 | 내용 |
| --- | --- |
| `index.html` | 페이지 전체 (챕터 · 연습문제 데이터 포함) |
| `editor.js` | CodeMirror 6 편집기 번들 |
| `py/pyodide.asm.wasm` | Pyodide 314.0.7 엔진 |
| `py/python_stdlib.b64.txt` | Python 표준 라이브러리 |
| `py/wheels.b64.txt`, `py/sql.b64.txt` | 브라우저에 설치할 패키지 (FastAPI, Pydantic, Jedi / SQLAlchemy, SQLModel) |
| `py/runner.txt` | 실행 · 실행 추적 · 채점 코드 |

## 라이선스 고지 · License notices

챕터 내용과 예제는 [FastAPI 공식 문서](https://fastapi.tiangolo.com/)(MIT, © Sebastián Ramírez)를 바탕으로 정리했습니다. 함께 배포하는 Pyodide · CPython 표준 라이브러리 · FastAPI 등 Python 패키지 · CodeMirror · Material Symbols의 저작권 표시와 라이선스 전문은 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)에 있습니다.

The chapter content and examples are adapted from the [FastAPI documentation](https://fastapi.tiangolo.com/) (MIT License, © Sebastián Ramírez). Copyright notices and full license texts for the bundled third-party components are in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). These components are Pyodide, the CPython standard library, FastAPI and other Python packages, CodeMirror, and Material Symbols.
