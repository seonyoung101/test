# 룸 오브 에러 (Room of Errors) 시뮬레이션

병실 그림에서 환자 안전을 위협하는 오류 11개를 찾아 클릭하는 웹 시뮬레이션입니다.
설치나 빌드 없이 `index.html` 파일 하나로 동작합니다.

## GitHub Pages로 실행하기

1. GitHub에서 새 저장소를 만듭니다. (예: `room-of-errors`)
2. `index.html`, `README.md`를 저장소 최상위에 업로드합니다. (Add file → Upload files)
3. 저장소의 **Settings → Pages**로 이동합니다.
4. **Build and deployment → Source**를 `Deploy from a branch`로 두고,
   Branch를 `main` / `/ (root)`로 선택한 뒤 **Save**를 누릅니다.
5. 1~2분 뒤 아래 주소로 접속합니다.

```
https://<GitHub 아이디>.github.io/<저장소 이름>/
```

## 내 컴퓨터에서 실행하기

- `index.html`을 더블클릭해 브라우저로 열면 됩니다.
- 또는 터미널에서 아래 명령 후 `http://localhost:8000` 접속:

```bash
python3 -m http.server 8000
```

## 사용법

| 기능 | 설명 |
|---|---|
| 시간제한 모드 | 3 / 5 / 8분 중 선택 |
| 연습 모드 | 시간 제한 없음 |
| 힌트 | 최대 3회, 회당 -3점 |
| 오답 클릭 | 회당 -2점 |
| 결과 화면 | 놓친 오류 표시, 오류별 해설, 디브리핑 질문 |

점수 = (발견 수 / 전체 수 × 100) − 오답 클릭 × 2 − 힌트 × 3 (최소 0점)

## 오류 수정·추가하기

`index.html`에서 두 곳만 고치면 됩니다.

1. `<script>` 안의 `ERRORS` 배열에 항목 추가

```js
{ id:'oxygen', cat:'환경 안전', title:'산소통이 고정되지 않음', why:'넘어지면 ... 해설 ...' }
```

2. SVG의 `#hits` 안에 같은 `id`로 클릭 영역 추가 (x, y, width, height는 900×520 좌표 기준)

```html
<rect data-err="oxygen" x="100" y="300" width="40" height="90"/>
```

장면 그림(병상, 모니터 등)은 `<svg id="scene">` 안의 도형을 수정하면 바꿀 수 있습니다.
시나리오 문구(환자 이름, 알레르기 등)는 시작 화면의 문단과 화이트보드 `<text>`에 있습니다.

## 포함된 오류 목록

손목밴드 불일치 · 알레르기 약물 투약 · 침상 난간 · 바퀴 잠금 해제 · 수액줄 늘어짐 ·
바닥 물기 · 모니터 알람 꺼짐 · 약 방치 · 호출벨 · 빈 손소독제 · 일반 폐기물통의 주사바늘
