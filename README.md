# Masonry Layout
Masonry Layout component wrap images to make them order from left to right. I have try 3 approach to create this component.

Images that used in this example come from [Lorem Picsum](https://picsum.photos/)
## setup
install and start server using command:
```
npm install
npm run dev
```

### MasonryGrid Component
For this component, I set the width of grid's row to 100px and add dynamic style to each grid items to span based on their height using `grid-row: [image height / 100]px`

**cons**
- need to adjust image width before placing to grid
- not flexible

### MasonryColumn Component
For this component, I set `column-count: [number]`
**cons**
- elements are not order from left to right

### MasonryGridTP Component
I use masonry layout by add `grid-template-rows: masonry;` property which is Level 3 of the CSS grid layout. More info at this [docs](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Masonry_layout#browser_compatibility).
**cons**
- This is an experimental technology
- Currently can be used in Safari or Firefox version 77 with preferences changing