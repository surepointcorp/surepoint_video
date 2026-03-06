# SurePoint AI-FL 영상 웹사이트 삽입 가이드

## 1. 파일 구성

영상 구현에 필요한 파일 목록입니다.

| 파일 | 설명 |
|------|------|
| `index.html` | 전체 영상 애니메이션 (단독 실행 가능) |
| `surepoint_ai_fl.mp4` | 녹화된 MP4 영상 파일 (38초) |
| `logo.png` | 검정 배경용 로고 |
| `logo_w.png` | 흰색(어두운 배경용) 로고 |
| `forklift_safe.jpg` | 파란색 LED 이미지 |
| `forklift_detect.jpg` | 빨간색 감지 이미지 |
| `forklift_warehouse.jpg` | 창고 배경 이미지 |

---

## 2. 방법 A — HTML 애니메이션을 섹션에 삽입 (권장)

기존 웹사이트의 특정 섹션에 `<iframe>`으로 삽입하는 방법입니다.

```html
<!-- 기존 웹사이트 HTML 내 원하는 위치에 삽입 -->
<section class="product-video-section">
  <iframe
    src="./forklift_video/index.html"
    width="100%"
    height="600px"
    frameborder="0"
    allowfullscreen
    style="border-radius: 12px; overflow: hidden;"
  ></iframe>
</section>
```

**CSS 예시 (반응형):**
```css
.product-video-section {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 60px 20px;
}

.product-video-section iframe {
  width: 100%;
  aspect-ratio: 16 / 9;
  height: auto;
  border-radius: 12px;
  box-shadow: 0 20px 60px rgba(0,0,0,0.3);
}
```

---

## 3. 방법 B — MP4 영상 파일을 `<video>` 태그로 삽입

```html
<section class="product-video-section">
  <video
    src="./surepoint_ai_fl.mp4"
    autoplay
    loop
    muted
    playsinline
    style="width: 100%; border-radius: 12px;"
  ></video>
</section>
```

> **참고:** MP4 방식은 CSS 애니메이션 효과(파티클, 스캔라인 등)가 포함되지 않습니다.
> 인터랙티브 효과(씬 전환, 클릭 등)가 필요하면 방법 A(iframe)를 사용하세요.

---

## 4. 방법 C — 코드를 직접 기존 페이지에 통합

`index.html`의 `<style>`, HTML 구조, `<script>` 블록을 기존 페이지에 직접 복사하여 통합할 수 있습니다.

단, 이 경우 CSS 클래스 이름 충돌에 주의하고, `.scene`, `.hud` 등의 클래스에 고유한 prefix를 붙이는 것을 권장합니다.

---

## 5. 영상 파일 저장 위치

- **HTML 애니메이션:** `/forklift_video/index.html` (+ 이미지/로고 파일 동봉)
- **MP4 영상:** `/forklift_video/surepoint_ai_fl.mp4` (38초, 1280×720, 3.1MB)
