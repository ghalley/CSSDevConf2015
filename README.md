# CSS DevConf

## Opening Keynote

### SVG for web designers/devs
http://www.slideshare.net/SaraSoueidan/svg-for-web-designers-and-developers

Author of:
- Coddrops CSS Reference
- Smashing Book 5

SVG articles: sarasoueidan.com/articles

Don't avoid SVG just to support IE8, use a fallback.
SVG is best for user controls, logos, icons, and illustrations.
- Icon Systems
- Ad Banners
- Infographics
- Data Visualizations
- Animated Illustrations
- Filter effects
- Simple UI shapes

Usually a knowledge gap between designers and developers around exported SVG code.

Simple shapes are easier to manage/maintain/animate (instead of paths).

Simplify paths:
- Each point is a pair of points in the path data

Combine paths where possible, if you don't need to animate them seperately.

Use good grouping, layering, and naming conventions.

Keep width and height attributes on `<svg>`

SVGO - a tool for optimizing SVG code

SVG JS animation library
- GreenSock Animation Platform (GSAP)
- Snap.svg
- Velocity.js

## Cracking the SVG Code
@brendamarienyc
Stickers!
Girl Develop It!

http://brendastorer.com/presentations/2015-10-CSSDevConf-SVGs/#intro

SVG has similarities to HTML:
- Unicode chars
- elements, tags, attr
- white space not important
- nesting
- bitmaps, anchors, text

SVG adds shapes, paths, opacity, gradients, rotation, animation

### Namepsacing
- semantic meatning for the name of the element and children
- value can be any string, usually url
- `xmlsn:xlink` just a unique identifier

### Viewport
- Units can be em, ex (height of x character), px, pt, pc
- Shapes inside of svgs use/inherit same units

### SVG Coordinate System
- start x, start y, end x, end y
- starts at top left corner

### Shapes
#### Rectangle
Has a width, height, rx, ry (rounded edges), fill, and stroke

#### Circle
Has radius (r), cx and cy (coordinates)

#### Ellipse
Adds rx and ry to circle

#### Line
Two sets of points (x1, y1, x2, y2)

#### PolyLine
Series of points: points

### Virtual Pen
#### Path
d for draw
Has types of lines:
(uppercase referes to viewport, lower refers to where last thing stopped drawing)
- M/m = moveto(x,y)
- L/l = lineto(x,y)
- A/a = arc
- C/c = curveto
- Z/z = close_path

##### Arc
- rx, ry
- x-axis-rotation sets rotation of arches
- large-arc-flag is boolean
- sweep-flag, clockwise or counterclockwise

Resources:
- SVG Compressed by Jakob Jenkov
- scriptdraw.com
- Pocket Guide to SVG by Joni


## Creative Typography with SVG Text
No auto line-wrapping

### `tspan`
-absolute positioning with x/y
-relative positioning with dx/dy

### Responsive SVG
viewBox + flexible container

### Curved Text

#### `textpath`
set text along arbitrary path

#### defs
definte reusable svg componants

SVG on MDN
jenkov.com SVG Tutorials
talks.brennaobrien.com/svg-typography

## Web Components
Why care about web components?
- managing global names
- scoping/isolating styles
- specificity conflicts
- unpredictable matching
- managing dependencies
- removing unused code

CSS selectors determine how scalable code is

What are bad selectors?
- casts a wide net, likely clashes

CSS operates on too much DOM

How to change CSS to make it harder to screw up?
What is CSS missing?
- scope or isolate styles to set of DOM nodes
- abstract implementation details
- bundle a set of styles with markup and logic that depends on them

Hooray web components!

Benefits of platform-based solutions
- no extra knowledge neeeded
- no dependencies
- interoperability

### Anatomy of Web Components #webmod
#### Shadow DOM
- Subtree of DOM nodes that you can create on any HTML element
- Shadow nodes are private

#### Custom Elements
- initally defined as JS classes
- extend HTMLElement then registered on document
- typically create a shadow root

#### HTML Imports
way to package custom elements and dependencies

#### Templates
inert bits of DOM, not processed by the browser

github.com/philipwalton/talks
http://zastrow.co/speaking/css-dev-conf-2015/


## Visual Regression Testing #RegTest
https://www.dropbox.com/s/yfn2vw8bjfmyyiu/visual-regression.pdf?dl=0

Basically testing pixels, not css or html (at it's purest form)

### Workflows
- Comparison
- Baseline

[Lonely Planet Styleguide](http://rizzo.lonelyplanet.com/styleguide/design-elements/colours)

VR Testing isn't good at distinguishing change in content vs. change in styles.


## 2nd Keynote

### Designing Systems
- Style guides
    - Zombie style guides, unmaintened and unused

Style guides must be living in order to be useful

Single source of truth: DRY principle
- design tokens, units of design that make guides scalable

Design system should align your whole team

### Design Principles:
- Clarity
- Efficiency
- Consistency
- Beauty

Provide devs scalable and accessible code early in dev cycle to empower them.

Clarity > Brevity

speakerdeck.com/jina/designing-a-design-system


## Keynote Day 2: Designing Meaningful Animation

Great UI animation has both purpose and style!

### Animating with Style

Using principles of animation from Disney Animation book, summarized in a tumblr blog.

Create animation that feels a bit real, makes it feel relatable and familiar.

### Animation Principles
#### Timing & Spacing
Timing = duration

Spacing is more like the changes in speed, or easing.

Makes animtated objects appear to obey the laws of physics.

Establishes mood, emotion, and reaction.

Everything is better with cubic-beziers

www.cubic-bezier.com

#### Follow Through
Not everything stops at once
Overshoot the target a bit

#### Secondary Action
Additional action to exagerate/accentuate/support primary action.

### The Bigger Picture

#### Choreography
Designing all animations to feel logical and related

Similar objects should move in similar ways

Entrances inform exits
- comes in from bottom, should leave from the bottom

Matching velocities creates relationships between objects

Cohesive over consistent

### Finding your best moves
- find star interaction
- model real world things
- match design adjectives to animation styles
    - follow through -> energetic, friendly, bold, excited
    - squash and stretch -> playful
    - smaller movements -> calm and subtle
    - opacity and blurs -> soft, stable, quiet

Aim to build your own animation library, for consistency
- document categories of animation
- Document your building blocks
    - opacity, scale, color, depth, position, rotation

uianimationnewsletter.com
@vlh

## CSS Level 4 Selectors
@Jcutrell
@developertea
@whiteboardis

### Column combinator
- use double pipes `||`

### Pseudo Selectors
Time-dimensional
- current
- current(s)
- past
- future

Not yet supported.

- `drop`(active, valid, invalid)
    - all :drop classes select the drop target, not the draggable item
- `read-write`, `read-only`
- `placeholder-shown`
- `default`
- `indeterminate`, could have value, but doesn't yet
- `in-range/out-of-range`, any element that has a max/min attribute set'
- `valid/invalid`, can use regex in `input pattern` attribute
- `user-invalid`, same as valid/invalid, only after user has interacted with that input
- `required`/`optional`, tied to presence of required attribute
- `blank`, matches things that have only whitespace
- `dir(ltr)`
- `lang(zh)`,
- `any-link`
- `scope`
- `[foo="bar" i]`, case insesitivity
- `E >> F`, descendant combinator
- `not(s1, s2`
- `has(s1, s2)`, (doesn't ever work in browser CSS), selection based on cabinets
- `matches(s1, s2)`

## Bower Power
https://github.com/ecarlisle/bower-power

### Dependency Management Issues
KISS - Kill It & Start Screaming/Keep It Stunningly Simple
- efficent, cheaper, better products, happier teams

### What Bower does
1. Maintains dependency manifest
2. Fetches them when you need it
3. Tracks Dependencies
4. Integrates with everything

### Bower vs NPM?
Many similarities, unique strengths

Bower:
- Abstracts, separates concerns
- Uses a flat dependency tree
- Lives and breathes git
- establishes accountability

Often, more than expected gets installed
- usually gets the whole github repo of project
- you might discover something that way
- you can use anything you need
- add bower_components to .gitignore

## Fight the Zombie Pattern Library
https://speakerdeck.com/marcelosomers/fight-the-zombie-pattern-library-css-dev-conf-2015
http://j.mp/zombie-library-cssdevconf

@marcelosomers

> How do you keep building interfaces knowing that's what the world is like?

> Build systems not pages

Each deliverable is a design system.

Design with patterns

Design process breaks down with distributed devlopment

Have a pattern library early to cut down on wasted artifacts.

### Getting Started with your own
#### Take Inventory of what you have

##### What to document
- Base styles
- Components
- Page templates

#### Standardize

#### Document

##### Centralize your CSS

### Code review on the CSS

### Some helpful tools
CSS Documentation
- KSS

Static Site Generation
- Pattern Lab

Integrated
- SourceJS

PatternPack

## Closing Keynote - The art of being wrong
shoptalkshow.com
godaytrip.com

### Sooooo many technologies to choose from

Sometimes, ideas need to die after they become wrong (a.k.a. outdated)

### How we become wrong
- Have a really strong opinion on a really niche topic

#### McNamara's fallacy
- Measure whatever can be easily measured.  This is cool, as far it goes
- Disregard that which can't be easily measured, or give an arbitrary value, which is artificial and misleading
- presume that which can't be measured easily isn't very important.  Blindness
- That which can't be measured isn't real.  Suicide.

>Well, actually...

### Promote Better Discussions


