# Implementation Plan: Insurance Advisor Portfolio

## Overview

Integrate the insurance advisor portfolio into the existing `hailee-portfolio-website` project by adding section-wise HTML blocks to `index.html`, appending CSS to `styles.css`, and appending JavaScript to `main.js`. All new CSS classes are prefixed with `ia-` to avoid collisions. Existing Boxicons, Swiper, and ScrollReveal libraries are reused. Tests live in `hailee-portfolio-website/tests/`.

## Tasks

- [x] 1. Update `index.html` head and replace navbar
  - Update `<title>` to `Insurance Advisor | Health & Medical Insurance`
  - Replace the existing `<header class="header">` block with the `ia-navbar` header block from the design
  - Remove the existing bottom floating `.nav__menu` (it is replaced by the top sticky navbar)
  - _Requirements: 1.1, 1.4, 13.1, 13.4_

- [x] 2. Add Hero, About, and Services HTML sections
  - [x] 2.1 Insert Hero section HTML (`ia-hero`) into `<main>` as the first section, replacing the existing `home` section
    - Use the exact markup from design Block 3; CTA href points to `#ia-contact`
    - _Requirements: 2.1, 2.2, 2.3, 2.4, 2.5_
  - [x] 2.2 Insert About section HTML (`ia-about`) after the Hero section, replacing the existing `about` section
    - Include profile image, three stat boxes (10+ Years, 500+ Families, Always Available), bio paragraph, and "Contact Me" button
    - _Requirements: 3.1, 3.2, 3.3, 3.4_
  - [x] 2.3 Insert Services section HTML (`ia-services`) after About, replacing the existing `services` section
    - Include exactly four cards: Health Insurance Planning, Policy Comparison, Claim Assistance, 1:1 Consultation — each with a Boxicon, title, and description
    - _Requirements: 4.1, 4.2_

- [x] 3. Add Why Choose Me, Process, Testimonials, and Contact HTML sections
  - [x] 3.1 Insert Why Choose Me section HTML (`ia-why`) after Services
    - Include three benefit items: Simple Explanations, Honest Advice, Personalized Support — each with icon and description
    - _Requirements: 5.1, 5.2_
  - [x] 3.2 Insert Process section HTML (`ia-process`) after Why Choose Me
    - Include exactly four steps: Understand Your Needs, Compare Plans, Select the Best Option, Ongoing Support — each with number badge, title, and description
    - _Requirements: 6.1, 6.2_
  - [x] 3.3 Insert Testimonials section HTML (reusing existing `.testimonial__container.swiper` markup) after Process
    - Use insurance-relevant client names (Priya Sharma, Rahul Mehta, Anita Desai) and quotes; reuse `testimonial1-3.png`
    - _Requirements: 7.1, 7.2, 7.3_
  - [x] 3.4 Insert Contact section HTML (`ia-contact`) after Testimonials
    - Three cards: Phone (`tel:[phone_number]`), Email (`mailto:[email]`), WhatsApp (`https://api.whatsapp.com/send?phone=[whatsapp_number]&text=...`) with `target="_blank"`
    - _Requirements: 8.1, 8.2, 8.3, 8.4, 8.5, 8.6_

- [x] 4. Add Floating WhatsApp Button and Footer HTML
  - [x] 4.1 Insert the floating WhatsApp button (`ia-whatsapp-float`) just before `</main>` or after `</main>` but before `</body>`
    - Fixed position, links to same WhatsApp URL as Contact section, `target="_blank"`, `aria-label="Chat on WhatsApp"`
    - _Requirements: 9.1, 9.2, 9.4_
  - [x] 4.2 Insert Footer HTML (`ia-footer`) after `</main>`
    - Advisor name, tagline, LinkedIn/Instagram/Facebook social links, copyright notice
    - _Requirements: 10.1, 10.2, 10.3, 10.4_

- [x] 5. Checkpoint — Verify HTML structure
  - Open `index.html` in a browser and confirm all ten sections render without console errors. Ensure all tests pass, ask the user if questions arise.

- [x] 6. Append Navbar and Hero CSS to `styles.css`
  - Append the `ia-navbar` CSS block (sticky positioning, scroll-header shadow, logo, links, hamburger mobile styles, `ia-navbar__menu--open` transition)
  - Append the `ia-hero` CSS block (min-height 100vh, gradient background, `iaFadeInUp` keyframe animation, responsive typography at 992px)
  - _Requirements: 1.1, 1.2, 1.4, 1.5, 2.5, 2.6, 12.2, 12.4_

- [x] 7. Append About, Services, and Why Choose Me CSS to `styles.css`
  - Append `ia-about` CSS (two-column desktop layout at 992px, stat boxes, image sizing)
  - Append `ia-services` CSS (2-col mobile grid, 4-col desktop grid at 992px, card hover lift `translateY(-6px)` + box-shadow)
  - Append `ia-why` CSS (stacked mobile, 3-col grid at 630px, icon + text flex layout)
  - _Requirements: 3.5, 4.3, 4.4, 5.3, 12.1, 12.2, 12.3_

- [x] 8. Append Process, Contact, WhatsApp Button, Footer, and light-theme override CSS to `styles.css`
  - Append `ia-process` CSS (vertical timeline mobile with `::after` connector, horizontal timeline at 768px with `::before` connector)
  - Append `ia-contact` CSS (single-col mobile, 3-col grid at 630px, card styles, link hover)
  - Append `ia-whatsapp-float` CSS (fixed bottom-right, `z-index: var(--z-modal)`, scale hover transition)
  - Append `ia-footer` CSS (background `var(--first-color)`, social links, tagline, copyright)
  - Append light-theme overrides for all `ia-` sections
  - _Requirements: 6.3, 8.3, 9.1, 9.3, 10.4, 12.1, 12.2, 12.3_

- [x] 9. Checkpoint — Verify CSS rendering
  - Check all sections render correctly at 320px, 630px, 768px, and 992px+ viewport widths. Ensure all tests pass, ask the user if questions arise.

- [x] 10. Append JavaScript to `main.js`
  - [x] 10.1 Append `iaScrollHeader()` function and wire to `window scroll` event
    - Adds/removes `scroll-header` class on `#ia-navbar` when `scrollY >= 50`
    - _Requirements: 1.2_
  - [x] 10.2 Append hamburger menu toggle logic
    - Toggle `ia-navbar__menu--open` class on `#ia-navbar-menu` on button click; swap `bx-menu`/`bx-x` icon; close menu on nav link click
    - _Requirements: 1.4, 1.5, 1.6_
  - [x] 10.3 Append `iaScrollActive()` function and wire to `window scroll` event
    - Adds/removes `active-link` class on `.ia-navbar__link` elements based on scroll position
    - _Requirements: 1.3_
  - [x] 10.4 Append ScrollReveal `sr.reveal()` calls for all `ia-` sections
    - All durations ≤ 800ms; cover hero, about, services (interval 100ms), why (interval 150ms), process (interval 200ms), testimonials, contact (interval 100ms), footer
    - Guard with `if (typeof sr !== 'undefined')`
    - _Requirements: 3.5, 4.5, 5.3, 6.4, 7.4, 11.1, 11.2, 11.3_

- [x] 11. Set up test infrastructure
  - Create `hailee-portfolio-website/tests/unit/` and `hailee-portfolio-website/tests/property/` directories
  - Create `hailee-portfolio-website/tests/package.json` with `jest` and `fast-check` dependencies, and `jsdom` test environment
  - Create `hailee-portfolio-website/tests/setup.js` that loads `index.html` into jsdom and stubs `ScrollReveal`, `Swiper`, and `mixitup`
  - _Requirements: 13.1_

- [x] 12. Write unit tests for HTML structure
  - [x] 12.1 Create `hailee-portfolio-website/tests/unit/html-structure.test.js`
    - Test: navbar renders logo text and five nav links (Home, About, Services, Process, Contact)
    - Test: hero heading equals "Simplifying Health Insurance for You"
    - Test: hero subheading equals "Less confusion, more clarity in your financial protection"
    - Test: hero CTA button text is "Get in Touch" and href is `#ia-contact`
    - Test: about section contains `<img>` with `src="assets/img/about.jpg"` and exactly three stat boxes
    - Test: about "Contact Me" button href is `#ia-contact`
    - Test: services section contains exactly four `.ia-services__card` elements
    - Test: why section contains at least three `.ia-why__item` elements
    - Test: process section contains exactly four `.ia-process__step` elements
    - Test: testimonials section contains exactly three `.testimonial__card` elements
    - Test: contact section contains a `tel:` link, a `mailto:` link, and a WhatsApp link starting with `https://api.whatsapp.com/send?phone=`
    - Test: WhatsApp contact link has `target="_blank"`
    - Test: floating WhatsApp button has `position: fixed` (via computed style or class) and `aria-label`
    - Test: footer contains LinkedIn, Instagram, Facebook links and a copyright notice
    - Test: no new external CDN `<script>` or `<link>` tags are introduced beyond the existing ones
    - _Requirements: 1.1, 2.1, 2.2, 2.3, 2.4, 3.1, 3.3, 3.4, 4.1, 5.1, 6.1, 7.1, 7.2, 8.1, 8.2, 8.3, 8.4, 9.1, 9.2, 10.1, 10.2, 10.3, 13.4_

- [x] 13. Write unit tests for JavaScript behaviour
  - [x] 13.1 Create `hailee-portfolio-website/tests/unit/js-behaviour.test.js`
    - Test: `iaScrollHeader` adds `scroll-header` to `#ia-navbar` when `scrollY` is 50
    - Test: `iaScrollHeader` removes `scroll-header` from `#ia-navbar` when `scrollY` is 49
    - Test: clicking hamburger toggle adds `ia-navbar__menu--open` to `#ia-navbar-menu`
    - Test: clicking a nav link while menu is open removes `ia-navbar__menu--open`
    - Test: ScrollReveal `sr.reveal` is called at least once for each new `ia-` section selector
    - _Requirements: 1.2, 1.4, 1.5, 1.6, 11.1_

- [ ] 14. Write property-based tests
  - [ ] 14.1 Create `hailee-portfolio-website/tests/property/navbar.property.test.js`
    - [ ]* 14.1.1 Write property test for scroll header class (Property 1)
      - **Property 1: Scroll header class applied after 50px**
      - **Validates: Requirements 1.2**
    - [ ]* 14.1.2 Write property test for hamburger menu open state (Property 2)
      - **Property 2: Hamburger menu open state shows nav links**
      - **Validates: Requirements 1.4, 1.5**
    - [ ]* 14.1.3 Write property test for nav link click closes menu (Property 3)
      - **Property 3: Clicking a nav link closes the mobile menu**
      - **Validates: Requirements 1.6**
  - [ ]* 14.2 Write property test for hero viewport height (Property 4)
    - Create `hailee-portfolio-website/tests/property/hero.property.test.js`
    - **Property 4: Hero section fills full viewport height**
    - **Validates: Requirements 2.5**
  - [ ]* 14.3 Write property test for service card structure (Property 5)
    - Create `hailee-portfolio-website/tests/property/services.property.test.js`
    - **Property 5: Service cards contain required structure (icon, title, description)**
    - **Validates: Requirements 4.2**
  - [ ]* 14.4 Write property test for services grid columns (Property 6)
    - Add to `hailee-portfolio-website/tests/property/services.property.test.js`
    - **Property 6: Services grid is 2-col mobile, 4-col desktop**
    - **Validates: Requirements 4.4**
  - [ ]* 14.5 Write property test for why-choose item structure (Property 7)
    - Create `hailee-portfolio-website/tests/property/why.property.test.js`
    - **Property 7: Why Choose items contain required structure (icon, description)**
    - **Validates: Requirements 5.2**
  - [ ]* 14.6 Write property test for process step structure (Property 8)
    - Create `hailee-portfolio-website/tests/property/process.property.test.js`
    - **Property 8: Process steps contain required structure (number, title, description)**
    - **Validates: Requirements 6.2**
  - [ ]* 14.7 Write property test for process timeline layout (Property 9)
    - Add to `hailee-portfolio-website/tests/property/process.property.test.js`
    - **Property 9: Process timeline layout changes at 768px**
    - **Validates: Requirements 6.3**
  - [ ]* 14.8 Write property test for testimonial card structure (Property 10)
    - Create `hailee-portfolio-website/tests/property/testimonials.property.test.js`
    - **Property 10: Testimonial cards contain required structure (img, name, quote)**
    - **Validates: Requirements 7.2**
  - [ ]* 14.9 Write property test for contact link URI schemes (Property 11)
    - Create `hailee-portfolio-website/tests/property/contact.property.test.js`
    - **Property 11: Contact links use correct URI schemes (tel:, mailto:, https://api.whatsapp.com/send?phone=)**
    - **Validates: Requirements 8.1, 8.2, 8.3, 8.4, 8.5, 8.6**
  - [ ]* 14.10 Write property test for ScrollReveal duration (Property 12)
    - Create `hailee-portfolio-website/tests/property/scroll-reveal.property.test.js`
    - **Property 12: ScrollReveal animation duration does not exceed 800ms**
    - **Validates: Requirements 11.2**
  - [ ]* 14.11 Write property test for no horizontal overflow (Property 13)
    - Create `hailee-portfolio-website/tests/property/responsive.property.test.js`
    - **Property 13: No horizontal overflow at any supported viewport width (320px–1440px)**
    - **Validates: Requirements 12.3**

- [x] 15. Final checkpoint — Ensure all tests pass
  - Run `npm test` from `hailee-portfolio-website/tests/`. Ensure all tests pass, ask the user if questions arise.

## Notes

- Tasks marked with `*` are optional and can be skipped for a faster MVP
- Contact placeholders (`[phone_number]`, `[email]`, `[whatsapp_number]`) must be replaced with real values before deployment
- The existing bottom floating `.nav__menu` CSS in `styles.css` is left intact — it only applies to the original site's nav markup which is removed
- Property tests use `fast-check` with a minimum of 100 iterations (`numRuns: 100`) per property
- Each property test must include the comment tag: `// Feature: insurance-advisor-portfolio, Property N: <property_text>`
