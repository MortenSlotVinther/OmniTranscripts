# Harmonoid MDP Presentation Creation Guide for LLMs

## Critical: 16:9 Aspect Ratio Constraints
- **Viewport**: 1280x720px (16:9 widescreen)
- **Usable area**: 1140x620px (after padding: 50px vertical, 70px horizontal)
- **Overflow prevention**: Content exceeding these dimensions causes scrollbars
- **Font scaling**: Use clamp() for responsive sizing within viewport

## File Structure Requirements
```
PresentationName.mdp                    # Main presentation file
PresentationName/                       # Folder with EXACT same name
├── css/
│   └── presentation.css               # Required: Custom styles
├── images/                            # Optional: Referenced assets
└── data/                              # Optional: JSON/CSV data files
```

## MDP Syntax Rules
```markdown
# Title Slide
## Subtitle

<link rel="stylesheet" href="PresentationName/css/presentation.css">

---

<div class="slide">
<!-- Slide 1 content -->
</div>

---

<div class="slide compact">
<!-- Dense content slide -->
</div>
```

## Content Limits Per Slide Type

### Standard Slide (no scrollbars)
- **Title (h2)**: 1 line, max 50 characters
- **Subtitle (h3)**: 1 line, max 60 characters  
- **Bullet points**: 5-7 items, max 60 chars each
- **Paragraphs**: 2-3 sentences max (150 chars)
- **Total content lines**: 10-12 maximum

### Compact Slide (class="slide compact")
- **Title (h2)**: 1 line, max 40 characters
- **Bullet points**: 7-9 items, max 50 chars each
- **Tables**: 5 rows × 4 columns maximum
- **Font reduction**: 20% smaller than standard
- **Total content lines**: 15-18 maximum

### Dense Slide (class="slide dense")
- **Multiple sections**: 2-3 mini-sections
- **Lists**: 4 items per section
- **Grid layouts**: 2×2 or 3×2 maximum
- **Font reduction**: 30% smaller
- **Total content lines**: 20-25 maximum

## CSS Classes for Visual Hierarchy

### Container Classes
```css
.slide                  /* Standard slide container */
.slide.compact          /* Reduced padding, smaller fonts */
.slide.dense           /* Minimal padding, smallest fonts */
.slide.center          /* Vertically centered content */
```

### Typography Classes
```css
.hero-metric           /* Giant numbers: 4em */
.hero-subtitle         /* Supporting text under metrics */
.problem-number        /* Red large numbers: 3.5em */
.problem-text          /* Gray supporting text */
.investment-number     /* White on gradient: 3em */
.investment-detail     /* Small white text */
```

### Layout Classes
```css
.problem-grid          /* 3-column grid for stats */
.stack-visual          /* Vertical stack layers */
.comparison-table      /* 3-column comparison */
.competitive-matrix    /* 4×N grid matrix */
.team-grid            /* 3-column team cards */
.exit-container       /* 3-column exit paths */
.unit-container       /* Flexbox metrics row */
```

### Visual Effect Classes
```css
.key-point            /* Purple-bordered highlight box */
.urgent               /* Red gradient with shadow */
.success-metric       /* Green gradient box */
.investment-box       /* Purple gradient CTA */
.moat-layer          /* Hover-animated list item */
```

## Content Templates by Slide Type

### 1. Title Slide
```html
<div class="slide">
<h1>Product Name</h1>
<h2>Tagline (max 60 chars)</h2>
<p style="font-size: 1.3rem; color: var(--gray);">
<em>Secondary tagline</em>
</p>
<div class="investment-box">
  <div class="investment-number">€5M Series A</div>
  <div class="investment-detail">15% equity</div>
</div>
</div>
```

### 2. Problem Slide (3 metrics)
```html
<div class="slide compact">
<h2>The Problem</h2>
<div class="problem-grid">
  <div class="problem-card">
    <span class="problem-number">70%</span>
    <span class="problem-text">Failure rate</span>
  </div>
  <!-- 2 more cards max -->
</div>
<div class="key-point">One-line insight</div>
</div>
```

### 3. Comparison Table
```html
<div class="slide compact">
<h2>Title</h2>
<div class="comparison-table">
  <div class="comparison-row">
    <span class="comparison-label">Metric</span>
    <span class="comparison-us">Us</span>
    <span class="comparison-them">Them</span>
  </div>
  <!-- 4 more rows max -->
</div>
</div>
```

### 4. Competitive Matrix
```html
<div class="slide compact">
<h2>Competitive Landscape</h2>
<div class="competitive-matrix" style="font-size: 0.85rem;">
  <div class="matrix-header">Feature</div>
  <div class="matrix-header">Us</div>
  <div class="matrix-header">Them</div>
  <div class="matrix-header">Other</div>
  <!-- Max 5 feature rows -->
</div>
</div>
```

### 5. Team Slide
```html
<div class="slide">
<h2>The Team</h2>
<div class="team-grid">
  <div class="team-member">
    <div class="member-name">Name</div>
    <div class="member-role">Title</div>
    <div class="member-bio">One achievement</div>
  </div>
  <!-- Max 3 members -->
</div>
</div>
```

## Color Variables
```css
--primary-purple: #7658EC;
--success-green: #00D67E;
--urgent-red: #FF3366;
--dark-navy: #000050;
--gray: #6C757D;
```

## Font Size Guidelines (clamp syntax)
```css
/* Format: clamp(min, preferred, max) */
h1: clamp(2.2em, 5vw, 3.5em)      /* Title slides only */
h2: clamp(1.8em, 4vw, 2.8em)      /* All slides */
h3: clamp(1.4em, 3vw, 2em)        /* Subtitles */
p:  clamp(1.1em, 1.8vw, 1.4em)    /* Body text */
.compact: -20% all sizes           /* Dense slides */
```

## Inline Styles Guidelines
- **Grid layouts**: `display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; max-width: 700px; margin: 0 auto;`
- **Flexbox**: `display: flex; justify-content: center; gap: 2rem; margin: 2rem 0;`
- **Color overrides**: `style="color: var(--success-green)"` for emphasis
- **Spacing adjustments**: `style="margin-top: 1.5rem"` for vertical rhythm
- **Font size override**: `style="font-size: 0.85rem"` for dense content

## Content That Will Cause Scrollbars (AVOID)
1. **Tables**: >5 rows or >4 columns
2. **Lists**: >7 bullet points without `compact` class
3. **Titles**: Multi-line h2/h3 elements
4. **Grids**: >3×3 layout without size reduction
5. **Text blocks**: Paragraphs >3 sentences
6. **Images**: Height >400px
7. **Code blocks**: >10 lines
8. **Nested content**: >3 levels deep

## Responsive Breakpoints (Disabled in Presentation Mode)
- Presentation viewer handles sizing
- Don't use @media queries in custom CSS
- Use clamp() for fluid typography
- Use percentage/rem units, not px

## Generation Checklist
1. ✓ Create folder structure first
2. ✓ Write CSS with all custom classes
3. ✓ Link CSS in first slide: `<link rel="stylesheet" href="Name/css/file.css">`
4. ✓ Each slide in `<div class="slide">` wrapper
5. ✓ Use `compact` class for slides with >10 lines
6. ✓ Test each slide has <15 total content lines
7. ✓ No embedded `<style>` tags
8. ✓ All images referenced from `/images/` subfolder
9. ✓ Color variables used, not hex codes
10. ✓ Font sizes use clamp() for scaling

## Common Pitfall Solutions
- **Scrollbars appearing**: Add `class="compact"` to slide div
- **Content cut off**: Reduce font sizes by 20%
- **Tables too wide**: Limit to 3 columns, abbreviate headers
- **Lists overflowing**: Split into 2 columns using grid
- **Text too small**: Increase clamp() minimum value
- **Spacing issues**: Use margin-top/bottom, not padding

## Validation Rules
```javascript
// Maximum content per slide
const maxLines = hasCompactClass ? 18 : 12;
const maxCharsPerLine = 100;
const maxTableRows = 5;
const maxGridItems = 9;
const maxBulletPoints = hasCompactClass ? 9 : 7;

// Required structure
const hasCSS = exists(`${name}/css/*.css`);
const hasSlideWrapper = html.includes('class="slide"');
const noInlineStyles = !mdp.includes('<style>');
const correctAspectRatio = "16:9";
```

## Example Full Slide (No Scrollbar)
```html
<div class="slide compact">

<h2>Market Opportunity</h2>

<div class="problem-grid">
  <div class="problem-card">
    <span class="problem-number">€50B</span>
    <span class="problem-text">TAM 2025</span>
  </div>
  <div class="problem-card">
    <span class="problem-number">45%</span>
    <span class="problem-text">CAGR</span>
  </div>
  <div class="problem-card">
    <span class="problem-number">2027</span>
    <span class="problem-text">Market mature</span>
  </div>
</div>

<div class="key-point">
<strong>First-mover advantage expires in 18 months</strong>
</div>

</div>
```

This structure guarantees no scrollbars in 16:9 viewport at 1280x720px resolution.