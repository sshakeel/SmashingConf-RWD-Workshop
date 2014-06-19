
**Workshop files**
- https://github.com/ahume/responsive-roadtrip

# Guardian.co.uk Responsive Strategy
- Started with a brand new mobile only site
- worked up to different interfaces from there
![Responsive Design Architecture](/imgs/rwd-architecture.jpg?raw=true "Responsive Design Architecture")

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
- e.g. guardian.co.uk

**pros**
- fresh start

**cons**
- need lots of time
- politically difficult

# Design Prototyping

### Styleguides
- potential design deliverables
- (instead of focusing on how to make a web site) focus on tools needed for deisng/dev process
- spectrum from design to dev

### Style Tiles
- http://styletil.es
- sits between moodboards and precise mockups
- catalyst for discusssions about the goals of an interface

### Element collage
- http://danielmall.com/articles/rif-element-collages

### Style prototype
- http://sparkbox.github.io/style-prototype

### Common Themes
- modules
- components
- elements
- "don't design pages, design system of components"

### Concept: Atomic Design (google this)
1. atoms
2. molecules
3. organisms
4. templates
5. pages

### Framework: Pattern Lab for Atomic Design
- http://patternlab.io/
- Pattern Lab library framework (google this)
- Based on PHP, node.js, .NET

### Pattern Portfolio
- http://clearleft.com/thinks/onpatternportfolios/

# Navigation Patterns
- http://bradfrost.github.io/this-is-responsive/design-patterns

### Several Different Approaches
- Nav first Approach (mostly desktop)
- Content First Approach (mostly mobile)
- link to footer Approach (thesession.org)
- Menu Toggle (starbucks.com)
- Select menu (retreatsforgeeks.com)
- Progressive Disclosure (guardian.co.uk)
  - collect the items that cannot fit into visible nav into a menu toggle
  - hybrid full + menu toggle

# Browser Support

### Defining "Support"
- should work in *all* browsers
- fix bugs for the nth percentile
  - unless doing so is disproportionately costly

### Browser Groups
- graded browser support
- "Cutting the mustard"
  - XE.com has taken similar apporach with the new redesign
  - two buckets
  - simplified development
  - simplified language
- check out guardian's frontend code on github for JS related to browser support (http://github.com/guardian/frontend)
![Responsive JS](/imgs/responsive-js.jpg?raw=true "Responsive JS")

# Layout Media Queries

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
![Match Media Code](/imgs/match-media.jpg?raw=true "Match Media Code")

### Concept: Element queries
- vary layout based on parent element
- self contained components
- more flexibility
- umm...don't exist
- (can we use SASS for this?)

### Media Query Support
- all modern browsers
- not supported in IE8

### Flex-box
- decent support, IE 10 and 11
- Not ideal for layout
- use for self-contained components
- http://css-tricks.com/snippets/css/a-guide-to-flexbox/
- RTL orientation inherited from parent container (WOO!)
- Experiment: navigation with flex-box
  - add a mobile size view
  - stacked navigation using...
    ```
    	flex-direction: column-reverse;
    ```

### Grid Layout
- true source independent layout
- sets up grid on the page
- IE10/11, Chrome (behind flag)
- new syntax issues still resolving

**Example: Container**

```css
	.container {
		display: grid; 
		...
	}
```

- Framework: http://unsemantic.com/
- E.g.: https://github.com/ahume/responsive-examples/blob/master/grid-layout.html

### Dealing with IE8
- does cut the mustard (maybe?)
- does not support media queries

**Strategy: 1** 
- leave it
- send it a mobile layout
- cost of supporting is high
- look at your user stats

**Strategy: 2**
- polyfill media queries
- performance overhead

**Strategy: 3**
- IE 8 only stylesheet
- deliver layout CSS in conditional HTML comment for IE
  - XE.com has implemented this in the new redesign
- automate stylesheet creation
  - https://github.com/guardian/sass-mq

# Performance and Resilience
Most stuff taken from the presentation during the main conference
  - https://speakerdeck.com/andyhume/building-for-performance-and-resilience

### Performance Priority
1. core content
2. Enhancement (css, etc)
3. Leftovers

### Optimizing: First Byte
- DNS lookup -> TCP connect -> HTTP request (SSL handshake) -> Server time -> HTTP response
- HTTP redirects happen at HTTP request. They start again at DNS lookup.
  - So yeah, eliminate redirects

### Optimizing: Start Render
- HTML (pre-)Parser -> (remote JS) -> DOM Tree -> Render Tree -> Layout -> Paint
- remote JS breaks pre-parser
- Avoid blocking scripts
    - move scripts to end of body
    - OR use "async" and "defer" attributes in "script" tags (limited support)
- use critical CSS as inline
    - https://github.com/pocketjoso/penthouse

### Optimizing: Path to Render
- Path to render starts right after HTML and CSS is loaded
- What causes rendering issues?
  - no fallback (e.g. ie8)
  - blocking
  - blocking + timeout (timeout = network issues)
- Solution
  - Provide control over font loading
  - WebFontLoader
    - **insert picture here**
    - Requirements
      - never block rendering
      - avoid flash of fallback font
      - compress and subset fonts as much as possible
      - reduce http requests as much as possible
      - cache as aggressively as browsers allow
  - base64 encoding
  - defer fonts for second page
  - subsetting
    - fonts must be as small as possible
    - subset your primary character set
    - strip out any unecessary icon glyphs
  - Hinting
    - test things
    - deliver a readable web font or no web font
  - Caching
    - HTTP caching is vital

### Progressive Enhancement
- Modern browsers only
  - WOFF support only
    - localStorage available

**add image here**

# Responsive Design Images

### Images on the web
- flexible, scalable, adaptable using % and ems
- used as interface elements, content and decoration

### SVG Benefits
- Fully native to the web
- flexible, adaptable, dynamic
- the real image format
- less buggy

### Icon font benefits
- easy color variations
- good browser support
- has its drawbacks

### SVG/PNG with grunticon
- emerging best practice
- base64 encoded svgs

```javascript
if (browserSupportSVG()) {
	loadCSS(svgURL);

} else {
	loadCSS(pngURL);
}

```

### Responsive images: use cases
- resolution based selection
- viewport based selection
- device-pixel-ratio based selection
- art direction
- media feature/type

### New: Image element

```html
<img alt="description" src="pic1x.jpg" srcset="pic@1x.jpg 1x, pic@2x.jpg 2x">

```

```html
<img alt="description" src="pic-s.jpg" srcset="pic-s.jpg 640w, pic-l.jpg 1024w" sizes="(min-width: 350px) 50vw, 100vw">

```

### New: Picture element

**add image here**

- picture tag, srcset, polyfill: https://github.com/scottjehl/picturefill

### Conditional Loading
- enhance with extra content

### Ajax include pattern
- for Modular Content
- https://github.com/filamentgroup/Ajax-Include-Pattern/

# Responsive Tables
- Guardian.co.uk took the approach of eliminating information while maintaining classic table look
- As seen in their points table for FIFA World Cup 2014 points table

### Tables into graphs
- Vitaly showed an example of how you can turn tables into graphs in mobile resolution

### Titled Headers
- One example had table headers tilted at 45 degrees

### Tables with display filters for column
- Another example had a "Display" filter dropdown for checking on and off columns

### Example: NFL Playoffs
- http://www.sbnation.com/a/nfl-playoffs-2014
- 