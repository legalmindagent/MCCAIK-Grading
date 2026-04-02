# MCCAIK Grading Website Upgrade Prompt

Upgrade the index.html for Jerry McKaig Const. grading company website. The site is already built with a solid structure. Make it PREMIUM — smoother, more animated, better images, better mobile experience.

## Current State
- Single-page HTML with inline CSS
- Dark hero, earthy color scheme (clay, amber, forest)
- Sections: Hero, Location strip, Cloudland callout, Photo showcase, Equipment, Services, Why Us, Service Area, CTA, Contact, Footer
- Scroll-reveal animations
- Mobile responsive with hamburger menu
- Deployed at mccaik-grading.vercel.app

## What to Improve

### 1. HERO IMAGES — Replace Stock Photos
Replace ALL Unsplash/Pexels URLs with high-quality images of:
- **Cloudland Canyon** — the actual canyon, waterfalls, overlook views
- **Lookout Mountain** — ridge views, mountain roads, scenic highway
- **Kubota equipment** — real Kubota excavators and skid steers on job sites
- **Earth moving work** — grading in progress, finished driveways, cleared land

Use these high-res free sources:
- Unsplash: search "cloudland canyon", "lookout mountain tennessee", "kubota excavator", "earth grading"
- Pexels: search "excavation", "grading construction", "skid steer"

Make sure ALL images are:
- At least 1920px wide for hero/background images
- At least 800px for cards/showcase
- Properly compressed with `?auto=format&fit=crop&w=1920&q=85`

### 2. SMOOTHER ANIMATIONS
Add these CSS animations:

**Parallax scrolling on hero and section backgrounds:**
```css
.hero-bg, .cloudland-bg, .why-bg {
  will-change: transform;
}
```
Add JS parallax:
```javascript
window.addEventListener('scroll', () => {
  const scrolled = window.pageYOffset;
  document.querySelectorAll('[data-parallax]').forEach(el => {
    const speed = el.dataset.parallax || 0.3;
    el.style.transform = `translateY(${scrolled * speed}px)`;
  });
}, { passive: true });
```

**Counter animation on hero stats (30+, 1200+, etc.):**
```javascript
function animateCounter(el, target, duration = 2000) {
  let start = 0;
  const increment = target / (duration / 16);
  const timer = setInterval(() => {
    start += increment;
    if (start >= target) { el.textContent = target + (el.dataset.suffix || ''); clearInterval(timer); }
    else el.textContent = Math.floor(start) + (el.dataset.suffix || '');
  }, 16);
}
```
Trigger when hero stats come into view.

**Smooth image hover zoom on showcase:**
Already exists but make it smoother — add `will-change: transform` and use `transition: transform 1.2s cubic-bezier(.25,.46,.45,.94)`.

**Staggered reveal on service cards:**
Already has `.reveal-d1`, `.reveal-d2` delays. Add `.reveal-d3`, `.reveal-d4`, `.reveal-d5` with 0.6s, 0.75s, 0.9s delays.

**Typing effect on hero tagline** (optional, subtle):
The hero badge "◆ Lookout Mountain · Cloudland Canyon · Tri-State Region" could type in letter by letter.

### 3. KUBOTA EQUIPMENT SECTION — Make it Premium
- Use actual Kubota product images (kubotausa.com has press photos)
- Add model specs in a subtle way:
  - KX057-5: "12,000 lbs, 47.6 HP, 12'9" dig depth"
  - SVL65-2: "7,830 lbs, 68 HP, 2,100 lb rated capacity"
- Add a "Powered by Kubota" badge/logo somewhere
- Make equipment cards slightly larger with better image aspect ratios

### 4. PHOTO GALLERY — Add Lightbox
When clicking a showcase photo, open a full-screen lightbox with:
- Larger image view
- Left/right arrows to navigate
- Close button
- Touch swipe on mobile
Simple CSS/JS lightbox — no library needed.

### 5. MOBILE IMPROVEMENTS
- Make the phone number button sticky at the bottom on mobile (floating call button)
- Increase touch targets to minimum 48px
- Make the form inputs larger on mobile (min-height 48px)
- Add smooth scroll snap between major sections
- Test all animations work on iOS Safari

### 6. CONTACT FORM
- Replace `action="https://formspree.io/f/placeholder"` with a real Formspree endpoint
- OR add a simple form handler that emails jerry directly
- Add form validation with friendly error messages
- Add a success state: "Thanks! Jerry will call you back within a few hours."

### 7. SEO & PERFORMANCE
- Add Open Graph meta tags with a screenshot as og:image
- Add structured data (LocalBusiness schema) — already partially there in meta description
- Add `loading="lazy"` to all images below the fold (already done on showcase)
- Preload the hero background image for faster first paint
- Add a favicon (use the clay triangle logo as a .ico)

### 8. ADDITIONAL SECTIONS TO ADD

**Before/After Gallery** (between Showcase and Equipment):
Show 2-3 before/after project comparisons with a slider effect.

**Google Reviews Badge** (in Why Us section):
Show a "5 stars on Google" badge with star icons and review count.

**"Areas We've Worked" Map** (optional):
Simple static map showing pins in the tri-state area. Can use a Google Maps embed or a styled SVG map.

### 9. COLOR & TYPOGRAPHY — Keep Current
The earthy palette is perfect for a grading company:
- Clay/rust (#c4652a, #e07030)
- Amber/gold (#d4943c, #eab45c)
- Forest green (#3a6a3a)
- Cream/stone (#f0ebe2, #c4b8a6)
- Bebas Neue for headings, Outfit for body

Don't change these — they're already on brand.

### 10. KEEP IT FAST
- No frameworks, no build tools — pure HTML/CSS/JS
- Total page weight should stay under 2MB
- All images via CDN (Unsplash/Pexels auto-optimize)
- Minify CSS/JS inline

## Business Info (don't change)
- **Company:** Jerry McKaig Const.
- **Owner:** Jerry McKaig
- **Phone:** 423-322-2592 (cell), 706-398-1685 (office)
- **Email:** jmckaigconst@aol.com
- **Address:** 315 Scenic Hwy, Rising Fawn, GA 30738
- **Location:** Next to Cloudland Canyon, on Lookout Mountain
- **Services:** Grading, Excavation, Land Clearing, Drainage, Roads, Demolition
- **Equipment:** Kubota KX057-5, Kubota SVL65-2, Ford F-650, Ram HD
- **Service Area:** TN, GA, AL tri-state (Chattanooga region)
- **Experience:** 30+ years, 1,200+ projects
