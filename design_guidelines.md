# AI Competition Gap Finder - Design Guidelines

## Design Approach
**System-Based Design** inspired by modern productivity tools like Linear, Notion, and data-focused applications. This tool prioritizes clarity, efficiency, and professional presentation of AI-generated insights.

## Core Layout Structure

**Main Application Layout:**
- Two-column desktop layout: Left sidebar (280px) for navigation/history, main content area for analysis
- Mobile: Single column, collapsible sidebar via hamburger menu
- Container max-width: `max-w-7xl` for main content

**Key Sections:**
1. **Hero/Input Section** - Prominent search/input area for company details
2. **Analysis Dashboard** - Structured display of AI-generated gap analysis
3. **Results Cards** - Individual gap opportunities with actionable insights
4. **Sidebar** - Quick access to saved analyses, recent searches

## Typography System

**Font Family:** 
- Primary: Inter or System UI stack
- Monospace: JetBrains Mono for data/metrics

**Hierarchy:**
- Page Title: `text-3xl font-bold`
- Section Headers: `text-2xl font-semibold`
- Card Titles: `text-lg font-medium`
- Body Text: `text-base`
- Captions/Meta: `text-sm text-gray-600`

## Spacing System
Use Tailwind units: **2, 3, 4, 6, 8, 12, 16** for consistent rhythm
- Component padding: `p-6` or `p-8`
- Section spacing: `space-y-6`
- Card gaps: `gap-4`

## Component Library

**Input Section:**
- Large textarea for company/product description (`min-h-32`)
- Multi-input form for competitor names (add/remove functionality)
- Primary "Analyze Competition" button (prominent, `px-8 py-3`)
- Loading state with spinner during AI processing

**Analysis Results Display:**
- Header with company name and analysis timestamp
- Tabbed interface: Overview | Gaps Identified | Opportunities | Recommendations
- Each gap presented as expanded card with:
  - Gap title (bold, large)
  - AI-generated description
  - Impact rating (visual indicator)
  - Suggested actions (bullet list)

**Gap Cards:**
- White background with subtle border
- Rounded corners (`rounded-lg`)
- Padding: `p-6`
- Shadow on hover: `hover:shadow-md transition-shadow`
- Icon for gap category (market, product, pricing, positioning)

**Sidebar Components:**
- "New Analysis" button at top
- Recent analyses list (max 10, scrollable)
- Each item: company name, date, one-line summary
- Click to load previous analysis

**Data Visualization:**
- Simple bar charts for competitor comparison metrics
- Tag system for categorizing gaps (badges with `rounded-full px-3 py-1`)
- Priority indicators (High/Medium/Low with corresponding visual weight)

## Interaction Patterns

**Form Submission:**
- Disable button during processing
- Show inline progress: "Analyzing competitors..." → "Identifying gaps..." → "Generating insights..."
- Smooth transition to results view

**Results Navigation:**
- Sticky tab navigation when scrolling
- Smooth scroll to sections
- Expandable/collapsible detailed recommendations

**Error States:**
- Inline validation messages for empty inputs
- Graceful API error handling with retry option
- Toast notifications for successful saves

## Images

**Hero Section:**
- Abstract data visualization or network graph illustration (800x400px)
- Positioned behind input form with overlay treatment
- Subtle parallax effect on scroll

**Empty States:**
- Simple illustration when no analyses exist yet
- Icon-based placeholder for loading states

## Layout Specifications

**Desktop (lg:):**
- Sidebar: Fixed 280px width
- Main content: Flex-grow with max-width constraint
- Analysis cards: 2-column grid (`grid-cols-2`)

**Tablet (md:):**
- Collapsible sidebar
- Single column analysis cards

**Mobile:**
- Full-width layout
- Stacked components
- Bottom sheet for sidebar navigation

## Accessibility
- High contrast text (gray-900 on white, white on dark backgrounds)
- Focus states on all interactive elements (`focus:ring-2`)
- ARIA labels for icon-only buttons
- Keyboard navigation for tabs and cards
- Screen reader friendly status updates during AI processing

This design creates a professional, efficient interface that makes AI-powered competition analysis feel structured and actionable while maintaining visual clarity.