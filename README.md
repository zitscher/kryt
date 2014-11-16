# kryt
A simple, yet awesome grid generator system.


## Why kryt?
The main goal was to create a responsive grid system with balanced spacings between rows, columns and its containing elements. kryt is desinged to work with interchangeable elements but can also be used without them.

kryt is designed to create a simple and fully customizable grid for your website, based on a variable quantity of columns and a predefined gutter width.

## Settings
By default, kryt comes with four predefined widths and breakpoints. Each of them can be changed individually and both grid and column sizes will be recalculated automatically by your default LESS compiler.

```css
// kryt total columns
// -------------------------
@kryt-columns: 12;

// Desktop grid size
// large Screens
// -------------------------
@kryt-desktop-xl-width:	1220px;
@kryt-desktop-xl-gutter:  30px;
@kryt-desktop-xl-border:   2px;

// Desktop grid size
// small Screens
// -------------------------
@kryt-desktop-sm-width:	980px;
@kryt-desktop-sm-gutter: 20px;
@kryt-desktop-sm-border:  2px;

// Tablet grid size
// -------------------------
@kryt-tablet-width: 768px;
@kryt-tablet-gutter: 20px;
@kryt-tablet-border:  2px;

// Mobile grid size
// -------------------------
@kryt-mobile-width:  100%;
@kryt-mobile-gutter: 10px;
```

## Rows
Your grid is based on rows. Every single row contains one or several columns, but in total your predefined number of total colums for your grid. In the example below we asume having a grid based on twelve columns.

### Example Markup
```html
<div class="container">
	<div class="row">
		<div class="col-12">[...]</div>
	</div>

	<div class="row">
		<div class="col-6">[...]</div>
		<div class="col-6">[...]</div>
	</div>
</div>
```

### Example Grid
![image](images/grid-12.png)

## Columns
If you choose a grid width of `980px` and a column count of `12` you will get `60px` for each column in the grid.

### The calculation of columns
```css
@single-column-width: ((@gridwidth - @gutter) / @columns) - @gutter; //60px
```

You can use [this](http://gridcalculator.dk/#/980/12/20/20) handy page to calculate your own grid

## Calculating the grid 

Depending on the column count, the mixin `.generate-kryt` generates your grid based on your grid-width and gutter width variables. You can optionally pass the border parameter if your layout needs it.


```css
.generate-kryt(@kryt-desktop-sm-width, @kryt-desktop-sm-gutter);
```


## Responsive Grids
If you want your grid to be responsive, you can implement various breakpoints and call the `generate-kryt` mixin in between your predefined media queries

### Example
#### The breakpoints
```css
@desktop-xl:	~"only screen and (min-width: 1225px)";
@desktop-sm:	~"only screen and (min-width: 1025px) and (max-width: 1224px)";
@tablet:		~"only screen and (min-width:  768px) and (max-width: 1024px)";
@mobile:		~"only screen and (max-width:  767px)";
```

#### The media queries
```css
.container
  // base kryt settings
  [...]
  
  // Desktops
  // -------------------------
  // large Screens
  @media @desktop-xl {
    .generate-kryd(@kryt-desktop-xl-width, @kryt-desktop-xl-gutter, @kryt-desktop-xl-border);
  }

  // small Screens
  @media @desktop-sm {
    .generate-kryd(@kryt-desktop-sm-width, @kryt-desktop-sm-gutter, @kryt-desktop-sm-border);
  }

  // Tablets
  // -------------------------
  @media @tablet {
    .generate-kryd(@kryt-tablet-width, @kryt-tablet-gutter, @kryt-tablet-border);
  }

  // Mobiles
  // -------------------------
  @media @mobile {
    .generate-kryd(@kryt-mobile-width, @kryt-mobile-gutter);
  }

  // Print Layout
  // -------------------------
  @media print {
    .generate-kryd(@kryt-desktop-sm-width, @kryt-desktop-sm-gutter);
  }
}
```



## License
MIT-style license.