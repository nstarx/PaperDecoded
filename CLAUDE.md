# Research Papers Explained - Project Guide

## Overview
This project hosts accessible, beginner-friendly explanations of cutting-edge AI/ML research papers. Each paper is converted into an interactive HTML document with simple language, analogies, and visual elements.

## Project Structure
```
/vl-jepa/
├── index.html                    # Main landing page / paper directory
├── VL-JEPA-Explained.html        # VL-JEPA paper explainer
├── Attention-Explained.html      # Attention Is All You Need explainer
└── CLAUDE.md                     # This file
```

## Design System

### Colors (CSS Variables)
- `--primary: #2563eb` (Blue)
- `--secondary: #7c3aed` (Purple)
- `--accent: #06b6d4` (Cyan)
- `--success: #10b981` (Green)
- `--warning: #f59e0b` (Orange)

### Text Color Rules
**IMPORTANT: Never use red for text - it's hard to read!**
- Use **blue** (`#2563eb`, `#3b82f6`, `#60a5fa`) for emphasis/negative indicators
- Use **gray** (`--text-secondary`) for secondary text
- Red is only OK for backgrounds/gradients, NOT for text

### Citation Heatmap (Card Headers)
Card header colors are based on citation count (heatmap style):
- **Legendary (10,000+)**: Red `#dc2626` → `#b91c1c` - landmark papers
- **High (100-9,999)**: Orange `#f97316` → `#ea580c` - highly cited
- **Medium (30-99)**: Yellow `#eab308` → `#ca8a04` - moderately cited
- **Low (<30)**: Blue `#3b82f6` → `#1d4ed8` - new/emerging papers

This is set automatically via JavaScript `setCitationTiers()` function.

### Icons
Use **Google Material Icons** throughout:
```html
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
<span class="material-icons">icon_name</span>
```

### Fonts
- **Inter** for index page
- **Segoe UI / system-ui** for paper explainers

## Creating a New Paper Explainer

### 1. HTML Structure
Each explainer follows this structure:
- Header with title, subtitle, paper info
- Table of Contents section
- Multiple content sections with:
  - Section headers with Material Icons
  - Highlight boxes (`.highlight-box`, `.highlight-box.success`, `.highlight-box.warning`)
  - Analogy boxes (`.analogy`)
  - Key insight boxes (`.key-insight`)
  - Comparison grids (`.comparison-grid`)
  - Timeline items (`.timeline`)
  - Use case grids (`.use-case-grid`)
  - Stats grids (`.stats-grid`)
- Glossary section
- Key Takeaways section
- Learn More / Sources section
- Footer with paper citation

### 2. Content Guidelines
- **Audience**: Non-technical readers, no PhD required
- **Language**: Simple, avoid jargon, explain technical terms
- **Analogies**: Use real-world comparisons (sports, cooking, etc.)
- **Structure**: Build concepts progressively
- **Visuals**: Use flow diagrams, comparison cards, stat cards

### 3. Adding to Index
Update `index.html` to add new paper card with all required data attributes:
```html
<article class="paper-card"
    data-categories="category1,category2"
    data-year="2025"
    data-citations="45"
    data-read-time="15"
    data-date="2025-01-15"
    data-read-year="2025">
    <div class="paper-card-header">
        <div class="category">
            <span class="material-icons">icon</span>
            Category Name
        </div>
        <span class="reading-badge"><span class="material-icons">auto_stories</span> Read 2025</span>
        <span class="citation-badge"><span class="material-icons">format_quote</span> 45</span>
        <h3>Paper Title</h3>
        <div class="authors">Authors</div>
    </div>
    <div class="paper-card-body">
        <p class="description">Brief description...</p>
        <div class="paper-meta">...</div>
        <div class="paper-tags">...</div>
        <div class="paper-card-actions">
            <a href="Paper-Explained.html" class="btn btn-primary">Read</a>
            <a href="arxiv-link" class="btn btn-outline">Paper</a>
        </div>
    </div>
</article>
```

### Data Attributes Explained
- `data-categories`: Comma-separated list for topic filtering
- `data-year`: Publication year (for "Published" filter)
- `data-citations`: Citation count (determines header heatmap color)
- `data-read-time`: Reading time in minutes
- `data-date`: Full date for sorting (YYYY-MM-DD)
- `data-read-year`: Year when paper was read (for "Read in" filter)

### Index Page Features
- **Collapsible topic filters**: Click "Filter by Topic" to expand/collapse
- **Year filters**: "Published" (publication year) + "Read in" (reading year)
- **Sort options**: Most Recent, Oldest First, Most Cited, Read Time
- **Search**: Full-text search across all cards

### 4. Remove "Coming Soon" Status
When a paper is ready, remove:
- `.coming-soon` class from the card
- `<span class="coming-soon-badge">Coming Soon</span>`
- `disabled` from the Read button
- Update button text and link

## Available Categories
- `vision` - Computer Vision
- `language` - Language Models
- `multimodal` - Multimodal AI
- `self-supervised` - Self-Supervised Learning
- `robotics` - Robotics & Planning
- `productivity` - AI & Productivity
- `testing` - Software Testing
- `efficiency` - Model Efficiency
- `data` - Data Integration
- `security` - Code Security
- `federated` - Federated Learning
- `agents` - AI Agents
- `reasoning` - Reasoning
- `multi-agent` - Multi-Agent Systems

## Key Components Reference

### Highlight Box
```html
<div class="highlight-box">Content</div>
<div class="highlight-box success">Success content</div>
<div class="highlight-box warning">Warning content</div>
```

### Analogy Box
```html
<div class="analogy">
    <div class="analogy-title"><span class="material-icons">lightbulb</span> Analogy Title</div>
    <p>Analogy content...</p>
</div>
```

### Comparison Grid
```html
<div class="comparison-grid">
    <div class="comparison-card old">
        <h4><span class="material-icons">cancel</span> Old Way</h4>
        <ul><li>Point 1</li></ul>
    </div>
    <div class="comparison-card new">
        <h4><span class="material-icons">check_circle</span> New Way</h4>
        <ul><li>Point 1</li></ul>
    </div>
</div>
```

### Stats Grid
```html
<div class="stats-grid">
    <div class="stat-card">
        <div class="number">50%</div>
        <div class="label">Description</div>
    </div>
</div>
```

## Research Workflow
1. Fetch paper from arXiv (abstract page + HTML if available)
2. Search for additional explanations, blog posts, reviews
3. Identify key concepts, contributions, results
4. Create simple analogies for each concept
5. Structure content progressively (what → why → how → results)
6. Write HTML with all visual components
7. Update index.html with new card
8. Test in browser
