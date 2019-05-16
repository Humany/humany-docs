# CSS in Humany Widgets
*This documentation is intended for widgets in v4 implementations.*

## Commonly used classes
All of our classes are prefixed with `humany-` to make it easier to scope our CSS.

Class | Description
------|------------
`humany-link`|Base-class used for every link, except for links in guide content.
`humany-paragraph`|Container for a `h2` title and a `div` containing any passed html. e.g. used for rendering guides.
`humany-list`|Base-class used for every list, except for lists in guide content.
`humany-item-list`|Contains a `humany-paragraph` and a `humany-list`.
`humany-html`|Contains any content of html, e.g. guide bodies.


## Widget types
- [Inline](inline)
- [Floating](floating)
- [Bot](bot)


## TO-DO:
- [x] Components for all widget types
  - [x] Inline
  - [x] Floating
  - [x] Bot
- [ ] Primary, secondary
- [ ] Document usage of data-attributes
- [ ] Interactive classes `humany-phrase-present`, `humany-category-{{current route}}` etc..
- [ ] Transitionerna i floating.
- [ ] Trigger-knappar (bot, floating)

