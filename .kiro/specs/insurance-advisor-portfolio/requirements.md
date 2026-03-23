# Requirements Document

## Introduction

This feature adapts the existing `hailee-portfolio-website` project into a modern, responsive static portfolio website for a Health & Medical Insurance Advisor based in India. The output is section-wise HTML, CSS, and JavaScript code that integrates into the existing project structure (`index.html`, `assets/css/styles.css`, `assets/js/main.js`). The site covers eight content sections plus a floating WhatsApp button and footer, all built with plain HTML, CSS, and JavaScript — no frameworks or build tools required.

---

## Glossary

- **Website**: The static HTML/CSS/JS portfolio site being built.
- **Navbar**: The sticky top navigation bar with logo and section links.
- **Hero_Section**: The full-viewport introductory section with headline, subheading, and CTA.
- **About_Section**: The professional introduction section.
- **Services_Section**: The card-based section listing the advisor's four core services.
- **Why_Choose_Section**: The benefits highlight section.
- **Process_Section**: The step-by-step timeline section.
- **Testimonials_Section**: The static client testimonials section.
- **Contact_Section**: The section containing phone, email, and WhatsApp contact details.
- **Footer**: The bottom site footer with social links and copyright.
- **WhatsApp_Button**: The floating fixed-position WhatsApp shortcut button.
- **ScrollReveal**: The existing `scrollreveal.min.js` library already present in the project.
- **Visitor**: A person browsing the portfolio website.

---

## Requirements

### Requirement 1: Sticky Navbar

**User Story:** As a Visitor, I want a sticky navigation bar at the top of the page, so that I can jump to any section at any time without scrolling back to the top.

#### Acceptance Criteria

1. THE Navbar SHALL display the advisor's name/logo on the left and navigation links (Home, About, Services, Process, Contact) on the right.
2. WHILE the Visitor scrolls past 50px from the top, THE Navbar SHALL apply a visible box-shadow to indicate the sticky state.
3. WHEN a Visitor clicks a navigation link, THE Website SHALL smooth-scroll to the corresponding section.
4. WHEN the Visitor's viewport width is below 768px, THE Navbar SHALL collapse the navigation links into a hamburger menu toggle.
5. WHILE the hamburger menu is open, THE Navbar SHALL display the navigation links in a vertical dropdown.
6. WHEN a navigation link is clicked on mobile, THE Navbar SHALL close the hamburger menu automatically.

---

### Requirement 2: Hero Section

**User Story:** As a Visitor, I want a visually engaging hero section, so that I immediately understand the advisor's value proposition and can take action.

#### Acceptance Criteria

1. THE Hero_Section SHALL display the heading "Simplifying Health Insurance for You".
2. THE Hero_Section SHALL display the subheading "Less confusion, more clarity in your financial protection".
3. THE Hero_Section SHALL display a CTA button labelled "Get in Touch".
4. WHEN a Visitor clicks the CTA button, THE Website SHALL smooth-scroll to the Contact_Section.
5. THE Hero_Section SHALL occupy at least 100vh on all screen sizes.
6. WHEN the page loads, THE Hero_Section SHALL animate its heading, subheading, and CTA button using a fade-in-up entrance animation.

---

### Requirement 3: About Section

**User Story:** As a Visitor, I want to read a professional introduction about the advisor, so that I can assess their credibility and approach before reaching out.

#### Acceptance Criteria

1. THE About_Section SHALL display a professional profile image using `assets/img/about.jpg`.
2. THE About_Section SHALL display a short bio paragraph emphasising trust, clarity, and a customer-first approach.
3. THE About_Section SHALL display three stat boxes: years of experience, clients served, and a support availability indicator.
4. THE About_Section SHALL display a "Contact Me" button that smooth-scrolls to the Contact_Section.
5. WHEN the About_Section enters the viewport, THE About_Section SHALL animate its image and text content using ScrollReveal fade-in effects.

---

### Requirement 4: Services Section

**User Story:** As a Visitor, I want to see the advisor's services presented as cards, so that I can quickly understand what help is available.

#### Acceptance Criteria

1. THE Services_Section SHALL display exactly four service cards: "Health Insurance Planning", "Policy Comparison", "Claim Assistance", and "1:1 Consultation".
2. THE Services_Section SHALL display each card with an icon, a title, and a short description.
3. WHEN a Visitor hovers over a service card, THE Services_Section SHALL apply a visible lift/shadow transition to the card.
4. THE Services_Section SHALL arrange cards in a 2-column grid on mobile and a 4-column grid on desktop (min-width 992px).
5. WHEN the Services_Section enters the viewport, THE Services_Section SHALL animate each card using ScrollReveal fade-in-up effects.

---

### Requirement 5: Why Choose Me Section

**User Story:** As a Visitor, I want to see the advisor's key differentiators, so that I can decide whether to engage their services.

#### Acceptance Criteria

1. THE Why_Choose_Section SHALL display at least three benefit items: "Simple Explanations", "Honest Advice", and "Personalized Support".
2. THE Why_Choose_Section SHALL display each benefit with a distinct icon and a one-sentence description.
3. WHEN the Why_Choose_Section enters the viewport, THE Why_Choose_Section SHALL animate each benefit item using ScrollReveal staggered fade-in effects.

---

### Requirement 6: Process Section

**User Story:** As a Visitor, I want to see a step-by-step process overview, so that I know what to expect when working with the advisor.

#### Acceptance Criteria

1. THE Process_Section SHALL display exactly four numbered steps: "Understand Your Needs", "Compare Plans", "Select the Best Option", and "Ongoing Support".
2. THE Process_Section SHALL display each step with a step number, a title, and a short description.
3. THE Process_Section SHALL render the steps as a vertical timeline on mobile and a horizontal timeline on desktop (min-width 768px).
4. WHEN the Process_Section enters the viewport, THE Process_Section SHALL animate each step using ScrollReveal sequential fade-in effects.

---

### Requirement 7: Testimonials Section

**User Story:** As a Visitor, I want to read client testimonials, so that I can build trust in the advisor's services.

#### Acceptance Criteria

1. THE Testimonials_Section SHALL display exactly three static testimonial cards.
2. THE Testimonials_Section SHALL display each card with a client avatar image (using existing `assets/img/testimonial1.png`, `testimonial2.png`, `testimonial3.png`), a client name, and a feedback quote.
3. THE Testimonials_Section SHALL use the existing Swiper.js library for a touch-enabled carousel on mobile.
4. WHEN the Testimonials_Section enters the viewport, THE Testimonials_Section SHALL animate the carousel container using a ScrollReveal fade-in effect.

---

### Requirement 8: Contact Section

**User Story:** As a Visitor, I want to find the advisor's contact details in one place, so that I can reach out through my preferred channel.

#### Acceptance Criteria

1. THE Contact_Section SHALL display a clickable phone number link using the `tel:` URI scheme.
2. THE Contact_Section SHALL display a clickable email address link using the `mailto:` URI scheme.
3. THE Contact_Section SHALL display a clickable WhatsApp link using the `https://api.whatsapp.com/send?phone=` URI scheme with a pre-filled greeting message.
4. WHEN a Visitor clicks the WhatsApp link, THE Website SHALL open WhatsApp in a new browser tab.
5. WHEN a Visitor clicks the email link, THE Website SHALL open the default mail client.
6. WHEN a Visitor clicks the phone link on a mobile device, THE Website SHALL initiate a phone call.

---

### Requirement 9: Floating WhatsApp Button

**User Story:** As a Visitor, I want a persistent WhatsApp shortcut button, so that I can contact the advisor instantly from any section of the page.

#### Acceptance Criteria

1. THE WhatsApp_Button SHALL be fixed at the bottom-right corner of the viewport at all times.
2. THE WhatsApp_Button SHALL display the WhatsApp icon and link to the same WhatsApp URL used in the Contact_Section.
3. WHEN a Visitor hovers over the WhatsApp_Button, THE WhatsApp_Button SHALL apply a scale-up transition.
4. THE WhatsApp_Button SHALL remain visible and accessible on all screen sizes.

---

### Requirement 10: Footer

**User Story:** As a Visitor, I want a clean footer with social links, so that I can follow the advisor on social media.

#### Acceptance Criteria

1. THE Footer SHALL display the advisor's name and a short tagline.
2. THE Footer SHALL display social media icon links (LinkedIn, Instagram, Facebook).
3. THE Footer SHALL display a copyright notice.
4. THE Footer SHALL use the existing `--first-color` CSS variable for its background to remain visually consistent with the existing site theme.

---

### Requirement 11: Scroll Animations

**User Story:** As a Visitor, I want subtle scroll-triggered animations, so that the page feels polished and engaging.

#### Acceptance Criteria

1. THE Website SHALL use the existing `assets/js/scrollreveal.min.js` library for all scroll-triggered animations.
2. WHEN any section enters the viewport, THE Website SHALL trigger a fade-in or slide-in animation with a duration no greater than 800ms.
3. THE Website SHALL NOT apply scroll animations to elements that are already visible on initial page load above the fold.

---

### Requirement 12: Mobile Responsiveness

**User Story:** As a Visitor on a mobile device, I want the website to be fully usable, so that I can browse and contact the advisor from my phone.

#### Acceptance Criteria

1. THE Website SHALL be fully functional and readable at viewport widths from 320px to 1440px.
2. THE Website SHALL use CSS media queries consistent with the existing breakpoints in `assets/css/styles.css` (320px, 630px, 768px, 992px).
3. THE Website SHALL NOT require horizontal scrolling at any supported viewport width.
4. THE Website SHALL use the existing CSS custom properties (variables) defined in `assets/css/styles.css` for all colours, fonts, and spacing to maintain visual consistency.

---

### Requirement 13: Integration with Existing Project

**User Story:** As a developer, I want section-wise HTML, CSS, and JS code, so that I can integrate each section into the existing project files without rewriting the entire codebase.

#### Acceptance Criteria

1. THE Website SHALL provide HTML markup for each section as a self-contained block that can be inserted into `hailee-portfolio-website/index.html`.
2. THE Website SHALL provide CSS rules as additive styles that can be appended to `hailee-portfolio-website/assets/css/styles.css` without overriding existing rules.
3. THE Website SHALL provide JavaScript as additive functions that can be appended to `hailee-portfolio-website/assets/js/main.js` without conflicting with existing code.
4. THE Website SHALL reuse existing library references already present in `index.html` (Boxicons, Swiper, ScrollReveal) and SHALL NOT introduce new external CDN dependencies.
