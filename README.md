# 김종현 교수 홈페이지 (NGNS Lab)

Gamma 사이트(https://jhk-5uz5iqe.gamma.site/)를 GitHub Pages용 정적 웹사이트로 옮긴 것입니다.
빌드 도구 없이 HTML/CSS/JS만으로 되어 있어서, 이 폴더 그대로 GitHub에 올리면 됩니다.

```
homepage/
├─ index.html          ← 모든 콘텐츠 (여기만 수정하면 됨)
├─ assets/
│  ├─ css/style.css    ← 디자인
│  ├─ js/main.js       ← 메뉴, 탭, 검색, 자동 번호/개수
│  └─ img/             ← 이미지 (hero, profile, research, activities, contact, favicon)
├─ .nojekyll           ← GitHub Pages 설정 파일 (없어도 동작함)
└─ README.md
```

---

## 1. GitHub Pages에 배포하기

### 저장소 이름에 따라 주소가 달라집니다

| 저장소 이름 | 사이트 주소 |
| --- | --- |
| `<아이디>.github.io` | `https://<아이디>.github.io/` |
| 그 외 (예: `jhk-homepage`) | `https://<아이디>.github.io/jhk-homepage/` |
| `ngnslab` 조직 아래 저장소 (예: `jhk`) | `https://ngnslab.github.io/jhk/` |

모든 경로를 상대 경로로 작성했기 때문에 어느 방식이든 그대로 동작합니다.

### 방법 A — 웹 브라우저로 업로드 (git 몰라도 됨)

1. GitHub 로그인 → 오른쪽 위 **+** → **New repository**
2. 저장소 이름 입력, **Public** 선택 → **Create repository**
3. 생성된 페이지에서 **uploading an existing file** 클릭
4. `homepage` 폴더 **안의** 파일·폴더(`index.html`, `assets` 폴더 등)를 전부 끌어다 놓기
   - `homepage` 폴더 자체가 아니라 그 **내용물**을 올려야 `index.html`이 저장소 최상단에 위치합니다.
5. **Commit changes** 클릭
6. 저장소 **Settings → Pages** → Source: **Deploy from a branch**, Branch: **main** / **(root)** → **Save**
7. 1~2분 뒤 같은 화면 위쪽에 사이트 주소가 표시됩니다.

### 방법 B — git 명령어

```bash
cd homepage
git init -b main
git add .
git commit -m "Initial homepage"
git remote add origin https://github.com/<아이디>/<저장소이름>.git
git push -u origin main
```

그다음 방법 A의 6번(Settings → Pages)과 같이 설정합니다.

---

## 2. 콘텐츠 수정하기

모든 내용은 `index.html`에 있습니다. GitHub 웹에서 파일을 열고 연필(✏️) 아이콘으로 바로 수정해도 되고, 저장(Commit)하면 1~2분 뒤 사이트에 반영됩니다.

### 논문 추가

해당 목록(`<ol class="entries numbered">`)의 **맨 위**에 `<li>` 한 줄을 추가합니다.
**번호와 탭의 개수는 자동으로 계산**되므로 직접 고칠 필요가 없습니다.

```html
<!-- International Journal 목록 맨 위에 추가 -->
<li>Kim, J., Park, K. &amp; Lee, S., Paper Title Here, <em>IEEE Access. v.13</em>, pp.1-10, March 2026</li>
```

- 저널명은 `<em>...</em>`로 감싸면 기울임꼴이 됩니다.
- `&` 기호는 `&amp;`로 써야 합니다.

| 목록 | 찾을 위치 (`id`) |
| --- | --- |
| International Journal | `id="pub-ij"` |
| Domestic Journal | `id="pub-dj"` |
| International Conference | `id="pub-ic"` |
| Domestic Conference | `id="pub-dc"` |
| International Patents | `id="pat-int"` |
| Domestic Patents | `id="pat-dom"` |
| Technology Transfers | `id="pat-tt"` |

### 특허 추가

등록된 특허는 `class="registered"`와 배지를 붙이면 상단 "registered" 개수에 자동 반영됩니다.

```html
<li class="registered">특허 제목, 출원번호 0000000, 2025-01-01, 등록번호 0000000, 2026-01-01 <span class="badge">등록</span></li>
<li>출원만 된 특허 제목, 출원번호 0000000, 2025-01-01</li>
```

국제 특허의 배지 문구는 `Registered`입니다.

### 기술이전 추가

```html
<li><span>기술이전 제목</span><span class="year">2026</span></li>
```

### 이미지 교체

`assets/img/` 안의 파일을 **같은 이름**으로 덮어쓰면 됩니다 (가로 1200~1600px, JPG 권장).

---

## 3. 내 컴퓨터에서 미리보기

`index.html`을 더블클릭하면 브라우저에서 바로 열립니다. (글꼴은 인터넷에서 불러오므로 온라인 상태여야 원래 글꼴로 보입니다.)
