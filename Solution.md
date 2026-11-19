Here is a complete solution for Assignment 5.4, split into the design-token stylesheet (tokens.css), the component/layout stylesheet (styles.css), and the sample HTML page (index.html).

1. Design-Token Stylesheet (tokens.css)
This file defines all your reusable variables in :root (Steps 1–4).

CSS
:root {
  /* 1. Color Tokens */
  --color-primary: #2563eb;       /* Vibrant Blue */
  --color-primary-hover: #1d4ed8; /* Darker Blue for hover states */
  --color-secondary: #10b981;     /* Emerald Green */
  --color-bg: #f8fafc;            /* Light Slate Background */
  --color-surface: #ffffff;       /* Card/Component Background */
  --color-text: #0f172a;          /* Dark Slate Text */
  --color-text-muted: #475569;    /* Secondary/Muted Text */
  --color-border: #e2e8f0;        /* Subtle Border */

  /* 2. Spacing Tokens */
  --space-sm: 0.5rem;   /* 8px */
  --space-md: 1rem;     /* 16px */
  --space-lg: 2rem;     /* 32px */

  /* 3. Font-Size Tokens */
  --font-size-sm: 0.875rem; /* 14px */
  --font-size-base: 1rem;   /* 16px */
  --font-size-lg: 1.25rem;  /* 20px */
  --font-size-xl: 2rem;     /* 32px */

  /* Bonus: Border Radius & Shadow Tokens */
  --radius-md: 8px;
  --shadow-sm: 0 2px 4px rgba(0, 0, 0, 0.05);
}
2. Component & Layout Stylesheet (styles.css)
This file imports tokens.css and applies the variables to headings, buttons, and cards (Step 5).

CSS
@import url('tokens.css');

/* Base Reset & Page Layout */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: system-ui, -apple-system, sans-serif;
  background-color: var(--color-bg);
  color: var(--color-text);
  font-size: var(--font-size-base);
  line-height: 1.6;
  padding: var(--space-lg);
}

.container {
  max-width: 900px;
  margin: 0 auto;
}

/* Headings using Font-Size & Spacing Tokens */
header {
  margin-bottom: var(--space-lg);
}

h1 {
  font-size: var(--font-size-xl);
  color: var(--color-primary);
  margin-bottom: var(--space-sm);
}

h2 {
  font-size: var(--font-size-lg);
  color: var(--color-text);
  margin-bottom: var(--space-sm);
}

p {
  color: var(--color-text-muted);
  margin-bottom: var(--space-md);
}

/* Grid Layout for Cards */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: var(--space-lg);
}

/* Cards using Surface, Border, Spacing, and Shadow Tokens */
.card {
  background-color: var(--color-surface);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  padding: var(--space-lg);
  box-shadow: var(--shadow-sm);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

/* Buttons using Color, Spacing, and Font-Size Tokens */
.btn {
  display: inline-block;
  padding: var(--space-sm) var(--space-md);
  font-size: var(--font-size-sm);
  font-weight: 600;
  text-decoration: none;
  border: none;
  border-radius: var(--radius-md);
  cursor: pointer;
  transition: background-color 0.2s ease;
  text-align: center;
}

.btn-primary {
  background-color: var(--color-primary);
  color: #ffffff;
}

.btn-primary:hover {
  background-color: var(--color-primary-hover);
}

.btn-secondary {
  background-color: var(--color-secondary);
  color: #ffffff;
}
3. Sample Webpage (index.html)
This HTML document links to styles.css to showcase the design tokens in action.

HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Assignment 5.4 — CSS Variables & Design Tokens</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="container">
    <header>
      <h1>Design System Showcase</h1>
      <p>Demonstrating reusable CSS variables for colors, spacing, and typography.</p>
    </header>

    <main class="card-grid">
      <!-- Card 1 -->
      <article class="card">
        <div>
          <h2>Primary Component</h2>
          <p>This card uses medium and large spacing tokens along with the primary color token for its heading and action button.</p>
        </div>
        <button class="btn btn-primary">Primary Action</button>
      </article>

      <!-- Card 2 -->
      <article class="card">
        <div>
          <h2>Secondary Component</h2>
          <p>Consistent padding and font sizes keep this card aligned with the rest of the system while using the secondary color token.</p>
        </div>
        <button class="btn btn-secondary">Secondary Action</button>
      </article>
    </main>
  </div>
</body>
</html>
How to Verify Step 6 (Testing Your Tokens)
Open tokens.css and change --color-primary: #2563eb; to --color-primary: #9333ea; (Purple) and --space-lg: 2rem; to --space-lg: 3rem;.

Refresh index.html in your browser.

Both the <h1> heading and the .btn-primary button will immediately turn purple, and the outer page padding, card gaps, and internal card padding will expand simultaneously.