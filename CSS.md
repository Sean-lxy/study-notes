### Selector

### Position

### Custom Properties

### CSS Functions

### CSS Media Queries

### Flex

### Grid

CSS Grid 布局是一种二维的基于网格的布局方案，相较于以往的布局方案而言，彻底得改变了我们设计用户界面的方式。

##### Terminology

- Grid Container：应用 `display: grid` 的元素
- Grid Item：`Grid Container` 的直接子元素
- Grid Line：构成网格结构的分界线
- Grid Cell：网格单元格
- Grid Track：两条相邻网格线之间的空间

##### Properties

Container Properties:

1. display: grid | inline-grid;

2. `grid-template-columns` and `grid-template-rows`

3. `grid-template-areas`

4. `grid-template`

5. `column-gap` and `row-gap` and `grid-column-gap` and `grid-row-gap`

6. `gap` and `grid-gap`

7. `justify-items`

8. `align-items`

9. `place-items`

10. `justify-content`

11. `align-content`

12. `place-content`

13. `grid-auto-columns` and `grid-auto-rows`

14. `grid-auto-flow`

15. `grid`

    values:

    - none
    - <grid-template>
    - <grid-template-rows> / [auto-flow && dense?]  <grid-auto-columns>?

Children Properties:

1. `grid-column-start` and `grid-column-end` and `grid-row-start` and `grid-row-end`
2. `grid-column` and `grid-row`
3. `grid-area`
4. `justify-self`
5. `align-self`
6. `place-self`

Special Units and Functions:

- `fr units`
- `Sizing Keywords`
  - `min-content`
  - `max-content`
  - `auto`
  - `fit-content`
  - `fractional units`
- `Sizing Functions`
  - `minmax()`
  - `min()`
  - `max()`
- `repeat`
- `masonry`
- `subgrid`



[CSS Grid Complete Guide](https://css-tricks.com/snippets/css/complete-guide-grid/)

### Links

[CSS-TRICKS](https://css-tricks.com/)