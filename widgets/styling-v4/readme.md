# CSS in Humany Widgets
*This documentation is intended for widgets in v4 implementations.*

## Commonly used classes
All of our classes are prefixed with `humany-` to make it easier to scope our CSS.

Component | Class | Description
----------|-------|------------
Link|`humany-link`|Base-class used for every link, except for links in guide content.
Paragraph|`humany-paragraph`|Container for a `h2` title and a `div` containing any passed html. e.g. used for rendering guides.
List|`humany-list`|Base-class used for every list, except for lists in guide content.
Item list|`humany-item-list`|Contains a `humany-paragraph` and a `humany-list`.
Html|`humany-html`|Contains any content of html, e.g. guide bodies.


## Widget types
- [Inline](inline)
  - [Main layout](inline/#main-layout)
  - [Components](inline/#components)
  - [Interactive classes](inline/#interactive-classes)
- [Floating](floating)
  - [Main layout](floating/#main-layout)
  - [Components](floating/#components)
  - [Interactive classes](floating/#interactive-classes)
- [Bot](bot)
  - [Main layout](bot/#main-layout)
  - [Components](bot/#components)
- [General Examples](examples)
  - [Chat header button styles](examples/#chat-header-button-styles)

## To-do
- [x] Components for all widget types
  - [x] Inline
  - [x] Floating
  - [x] Bot
- [ ] Main layout
  - [x] Headers, content and footer
  - [ ] Primary and secondary in floating and inline
- [ ] Document usage of data-attributes
- [ ] Interactive classes
  - [x] Inline
  - [x] Floating
  - [ ] Bot
- [x] Transitionerna i floating.
- [ ] Trigger-knappar (bot, floating)
- [ ] Accordion guides (inline)

