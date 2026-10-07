# Engineering Challenges

## 1. Reveal animations without a library

**Challenge:** Sections should animate in when reached, in a direction that follows scroll.

**Resolution:** `IntersectionObserver` per section with a visibility threshold, and a passive scroll listener to record direction. Each effect disconnects or removes its listener on cleanup.

**Trade-off:** Several near-identical observer effects live in the Home component. A shared hook would reduce repetition.

## 2. Autoplaying background video

**Challenge:** Browsers restrict autoplay, and phones often force fullscreen playback.

**Resolution:** The video is muted, looping and `playsInline`, which allows autoplay on both desktop and mobile.

**Trade-off:** The video is the largest asset on the site. A poster image, a smaller encode or lazy loading would cut first-load weight.

## 3. Enquiries without a backend

**Challenge:** A static site still needs to deliver form submissions.

**Resolution:** The browser SDK of a hosted email service sends the form directly. The form validates required fields and email format first and shows success or error feedback.

**Trade-off:** There is no server-side validation, rate limiting or spam control of the project's own; those depend on the email service's settings. With any browser-side email service, the service identifiers necessarily reach the visitor's browser, so protection depends on restrictions configured with the provider.

## 4. A navigation bar that adapts to its backdrop

**Challenge:** The header sits over a dark video on Home and over light pages elsewhere.

**Resolution:** The bar reads scroll position and switches its colour treatment, with a collapsed menu button on narrow screens.

**Trade-off:** On the home page the fixed bar overlaps content while scrolling, which is a deliberate visual choice rather than a layout bug.
