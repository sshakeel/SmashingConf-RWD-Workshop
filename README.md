
# Workshop files
- https://github.com/ahume/responsive-roadtrip

# Gaudian Responsive Strategy
Guardian started with a brand new mobile only site
started working up from there


# Mobile first design
- simplify
- prioritize
- stealth design
- core html content first
- core styles first

# SEO
- Redirect performanace -> SEO complexity

# RWD Approaches 

### 1-Retrofitting
- refactor existing desktop site
- add stylesheets for smaller screens
- media in style tags

**pros**
- simple
- less design complocations
-politically simpler

**cons**
- might not be simple
- layout only focus
- performace
- requires media query support

### 2-Step by step
- incremental improv
- page by page
- component by compoenent
- eg. microsoft

**pros**
- politically simpler
- can prioritize most important parts
- learning as we go

**cons**
- consistency
- technical complexity

### 3-New Mobile Site
- leave existing 'desktop' site
- start mobile from scratch

**pros**
- politically simple
- starts with flexibility
- performance foocus
- layout scale up

**cons**
- still a separate site
- redirects, consistency, SEO
- scale up design can be hard

### 4-mobile first responsive
- start with mobile focus
- progressively enhance to desktop

**pros**
- fresh start

**cons**
- time
- politically difficult

# Design Prototyping

## Pattern Portfolio
- 

## Styleguides
- and variations
- potential design deliverables
- tools for deisng/dev process
- spectrum from design to dev

## Style Tiles
- http://styletil.es
- sit between oodboards and precise mockups
- catalyst for discusssions about the goals of an interface

## Element collage
- http://danielmall.com/articles/rif-element-collages

## Style prototype
- http://sparkbox.github.io/style-prototype
- into

## Common Themes
- modules
- components
- Elements
- "not designing pages, design system of components"

## Atomic Design
- atoms
- molecules
- organisms
- templates
- pages

## Pattern Lab 
- Pattern Lab library framework (google this sucker)
- php, node.js, .NET

# Navigation Patterns

- bradfrost.github.io/this-is-responsive/design-patterns

## Different Approaches
- Nav first Approach (mostly desktop)
- Content First Approach (mostly mobile)
- link to footer Approach (thesession.org)
- Menu Toggle (starbucks.com)
- Select menu (retreatsforgeeks.com)
- Progressive Disclosure (gaurdian.co.uk)
  - collect the items that cannot fit into visible nav into a menu toggle
  - hybrid full + menu toggle

# Browser Support

## Defining "Support"
- works in *all* browsers
- fix bugs for the nth percentile
  - unless doing so is disproportionaltely costly

## Browser Groups
- graded browser support
- Cutting the mustard
  - basically the apporach XE is taking
  - two buckets
  - simplified development
  - simplified language
- check out gaurdian's frontend code on github for browser support (github.com/gaurdian/frontend)

# Layout Media Queries

## Layout

### Pixels
- device pixels
- css pixels

### Viewports
- Visual Viewport
  - actual portion you can see on the screen
- Layout Viewport

### Meta Viewport
- viewport meta tag
  - layout = visual (mobile)
- @viewport {} (coming soon)

### Media Types
- print, screen, etc

### Media Queries
- CHaracteristics of browsing env
- screen, viewport size, etc
- viewport is all we have
- tightly couples components to viewport size
- discourages component based design/dev

### Match Media
- JS based media queries
- see picture on phone

### Element queries
- vary layout based on parent element
- self contained components
- more flexibility
- umm...don't exist
- (can we use SASS for this?)

### Media Query Support
- all modern browsers
- not supported in IE8
