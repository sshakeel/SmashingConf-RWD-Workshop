
**Workshop files**
- https://github.com/ahume/responsive-roadtrip

# Gaudian.co.uk Responsive Strategy
- Started with a brand new mobile only site
- worked up to different interfaces from there


### Mobile first design
- simplify
- prioritize
- stealth design
- core html content first
- core styles first

### SEO
- Bad redirect performance leads to SEO complexity 
- (Interesting claim. Did not receive a lot of details on this. Need to research this more.)

# RWD Approaches 

### 1- Retrofitting
- refactor existing desktop site
- add stylesheets for smaller screens
- could use media query in style tags in simpler cases
- e.g. current XE.com

**pros**
- simple
- less design complications
- politically simpler

**cons**
- might not be simple
- layout only focus
- performace concerns
- requires media query support

### 2- Step-by-step
- incremental improvment
- page by page
- component by compoenent
- eg. microsoft

**pros**
- politically simpler
- can prioritize most important parts
- learning as we go

**cons**
- consistency issues
- technical complexity

### 3- New Mobile Site
- leave existing 'desktop' site
- start mobile from scratch
- e.g. older XE.com mobile site

**pros**
- politically simple
- starts with flexibility
- performance focus
- layout scale up

**cons**
- still a separate site
- redirects and consistency issues, SEO
- scale up design can be hard

### 4-mobile first responsive
- start with mobile focus
- progressively enhance to desktop
- e.g. gaurdian.co.uk

**pros**
- fresh start

**cons**
- need lots of time
- politically difficult

# Design Prototyping

## Styleguides
- potential design deliverables
- (instead of focusing on how to make a web site) focus on tools needed for deisng/dev process
- spectrum from design to dev

## Style Tiles
- http://styletil.es
- sits between moodboards and precise mockups
- catalyst for discusssions about the goals of an interface

## Element collage
- http://danielmall.com/articles/rif-element-collages

## Style prototype
- http://sparkbox.github.io/style-prototype

## Common Themes
- modules
- components
- elements
- "don't design pages, design system of components"

## Concept: Atomic Design (google this)
1. atoms
2. molecules
3. organisms
4. templates
5. pages

## Framework: Pattern Lab 
- Pattern Lab library framework (google this)
- Based on PHP, node.js, .NET

## Pattern Portfolio
- http://clearleft.com/thinks/onpatternportfolios/

# Navigation Patterns
- http://bradfrost.github.io/this-is-responsive/design-patterns

## Several Different Approaches
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
- should work in *all* browsers
- fix bugs for the nth percentile
  - unless doing so is disproportionately costly

## Browser Groups
- graded browser support
- "Cutting the mustard"
  - XE.com has taken similar apporach with the new redesign
  - two buckets
  - simplified development
  - simplified language
- check out gaurdian's frontend code on github for JS related to browser support (http://github.com/gaurdian/frontend)

# Layout Media Queries

## Layout

### Pixels
- device pixels
- css pixels

### Viewports
- Visual Viewport
  - actual portion you can see on the screen
- Layout Viewport
  - controled by css

### Meta Viewport
- viewport meta tag
  - layout = visual (mobile)
- @viewport {} (coming soon - google this)

### Media Types
- print, screen, etc

### Media Queries
- Characteristics of browsing environment
- screen, viewport size, etc
- viewport is all we have
- tightly couples components to viewport size
- discourages component based design/dev
  - Opinion: This is where things should be headed in the future

### Match Media
- JS based media queries
- see picture on phone

### Concept: Element queries
- vary layout based on parent element
- self contained components
- more flexibility
- umm...don't exist
- (can we use SASS for this?)

### Media Query Support
- all modern browsers
- not supported in IE8