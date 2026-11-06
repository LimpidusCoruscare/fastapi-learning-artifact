# FastAPI 실습실

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

- 진도와 연습문제 초안은 **이 브라우저(localStorage)에만** 저장됩니다. 다른 기기와는 공유되지 않아요.
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
