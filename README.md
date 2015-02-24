# Arrange

Arrange is a very simple, flexible grid framework for quick-building, prototyping, or production-level code.  Its goal is to help you by doing as little as possible while staying out of your way.

## Getting Started

The first step to getting started with using Arrange is to include the CSS file on your page. You can do this with a call that looks like so:

```html
<link href="/path/to/arrange.css" rel="stylesheet">
```

> **Note:** you'll want to change the path of your `href` attribute to point to the actual file, wherever it's located on your server.

That's it, you should be good to go. Arrange doesn't have any JavaScript components to make it work, everything is contained in that one CSS file.


## Basic Usage
In its most basic for, *Arrange* will work something like this:

```html
<div class="row">
    <div class="four columns">
        <!-- this would be a 1/3-width column -->
    </div>
    <div class="eight columns">
        <!-- this would be a 2/3-width column -->
    </div>
</div>
```

What's happening here:

- An element with the class `row` wraps the columns you wish to set up, this element is responsible for clearing your columns (which are floated) so that as content in the columns expand, the row expands with it
- Child elements with the class `columns` and the number of columns to span are included within, each column element is being floated left

The important thing to note is that the number of columns used add up to twelve.

## Class Aliases

There are a couple of aliases in place to let you use the words that make sense to you.

- You can use the class `row` or `container` for the element holding columns
- You can use the class `columns` or `column` for the elements that are spanning columns
- Rather than specifying the number of columns to span, you can also use the width that you're trying to accomplish with the following helpers:
   - `one` can be `twelfth` or `one-twelfth`
   - `two` can be `sixth` or `one-sixth`
   - `three` can be `quarter` or `fourth` or `one-quarter` or `one-fourth`
   - `four` can be `third` or `one-third`
   - `six` can be `half` or `one-half`
   - `eight` can be `two-thirds`
   - `nine` can be `three-quarters` or `three-fourths`
   - `twelve` can be `full`

These classes have been included to work with the different ways that you might think about column widths. If you choose to use the fraction-based names, instead of columns adding up to twelve, they should total to one.


## Nesting Grids
Grids can be nested. That might look something like this:

```html
<div class="row">
    <div class="four columns">
        <!-- this would be a 1/3-width column -->
    </div>
    <div class="eight columns row">
        <!-- this would be a 2/3-width column that can hold its own columns -->
        <div class="six columns">
            <!-- this would be 1/2-width of the 2/3-width column -->
        </div>
        <div class="six columns">
            <!-- this would also be 1/2-width of the 2/3-width column -->
        </div>
    </div>
</div>
```

> **Note:** the column in the first set of columns that will be holding sub-columns also has a the `row` class applied to it. This will enable that column to expand to the sub-columns that it holds.


## Offsets

If you want to leave some white space between columns, you'll use the `offset` classes. These use the same set of numbers and number-aliases above, but are prepended by `offset-by-`. For example, let's say you wanted to have two columns, but leave a little room between them, you might do something like this:

```html
<div class="row">
    <div class="six columns">
        <!-- this would be a 1/2-width column -->
    </div>
    <div class="five columns offset-by-one">
        <!-- this would be a 5/12-width column pushed over a 1/12-width column -->
    </div>
</div>
```

This is a full row (because `six` plus `five` plus the offset-by-`one` makes twelve).


## Responsiveness

*Arrange* doesn't try to handle responsiveness out-of-the-box; it only handles laying out columns into a flexible grid. That is by design. Grid columns can be made responsive through media queries, but that all must be done manually, as it isn't something that can be properly guessed out-of-the-box.

Use break points that make sense to your project and adjust from there.


## Reverse Order

Sometimes for responsiveness you don't want your left columns coming before your right columns. This is where `reverse` comes in. By specifying this class on your `row` element, columns within will float right instead of left, reversing the order that they show up on the page.

This would work like this:

```html
<div class="reverse row">
    <div class="four columns">
        <!-- this would be a 1/3-width column -->
    </div>
    <div class="eight columns">
        <!-- this would be a 2/3-width column -->
    </div>
</div>
```

> **Note:** in the CSS file itself, the reverse classes are the second section of `arrange.css`. If you aren't going to use the reverse classes, it is recommended this section from the file to save on file-size.


## Off-Grid Equal-Width Columns

Sometimes you'll need to break out of the twelve-column system, and *Arrange* gives you the tools to do so. Included with the standard columns are the following off-grid systems, each with their own class aliases for determining column widths:

- One-fifth columns, with the following available classes:
   - `one-fifth` or `fifth` for column width, `offset-by-one-fifth` or `offset-by-fifth` for offset
   - `two-fifths` for column width, `offset-by-two-fifths` for offset
   - `three-fifths` for column width, `offset-by-three-fifths` for offset
   - `four-fifths` for column width, `offset-by-four-fifths` for offset
- One-seventh columns, with the following available classes:
   - `one-seventh` or `seventh` for column width, `offset-by-one-seventh` or `offset-by-seventh` for offset
   - `two-sevenths` for column width, `offset-by-two-sevenths` for offset
   - `three-sevenths` for column width, `offset-by-three-sevenths` for offset
   - `four-sevenths` for column width, `offset-by-four-sevenths` for offset
   - `five-sevenths` for column width, `offset-by-five-sevenths` for offset
   - `six-sevenths` for column width, `offset-by-six-sevenths` for offset
- One-eighth columns (which can be used in conjunction with `one-fourth` and `half` columns)
   - `one-eighth` or `eighth` for column width, `offset-by-one-eighth` or `offset-by-eighth` for offset
   - `three-eighths` for column width, `offset-by-three-eighths` for offset
   - `five-eighths` for column width, `offset-by-five-eighths` for offset
   - `seven-eighths` for column width, `offset-by-seven-eighths` for offset
- One-ninth columns (which can be used in conjunction with `one-third` and `two-thirds` columns)
   - `one-ninth` or `ninth` for column width, `offset-by-one-ninth` or `offset-by-ninth` for offset
   - `two-ninths` for column width, `offset-by-two-ninths` for offset
   - `four-ninths` for column width, `offset-by-four-ninths` for offset
   - `five-ninths` for column width, `offset-by-five-ninths` for offset
   - `seven-ninths` for column width, `offset-by-seven-ninths` for offset
   - `eight-ninths` for column width, `offset-by-eight-ninths` for offset

### Notes on these Special Columns

- In the CSS file itself, the these classes are grouped together into a [perforated section](Arrange#reducing-file-size); if you aren't going to use these classes, it is recommended this section from the file to save on file-size
- Each of these sets comes with the same `reverse` option as that of the standard columns
- The set of `one-eighth` columns don't include widths and offsets for even numbers; for those, you should use the `one-fourth` columns and offsets that come with the standard grid
- These are called "off-grid" columns because they don't align to the twelve-column grid; each of these sets will work best by themselves (with the noted exception of the `one-eighth` columns); these will, however, work fine on their own or as sub-columns within standard-columned layouts


## Collapsed Grids

*Arrange* also comes with all of the features listed above in a format that doesn't use gutters. To remove the gutters from any grid, simply add the `collapsed` class to the container element (the element with a class of either `row` or `container`). Like this:

```html
<div class="row collapsed">
    <div class="four columns">
        <!-- this would be a 1/3-width column -->
    </div>
    <div class="eight columns">
        <!-- this would be a 2/3-width column -->
    </div>
</div>
```

## Reducing File Size

As noted in some of the above sections, the full code of *Arrange* is perforated into six sections:

- The core grid with offsets
- The collapsed grid with offsets
- Reverse grid styles
- Reverse collapsed styles
- Off-grid equal-width columns
- Collapsed off-grid equal-width columns

If you're going to use gutters, only the *core grid with offsets* section is needed. If you're going to not use gutters, only the *collapsed grid with offsets* is needed. The rest of the sections can be removed to save on file size. To find the perforation points, find the following line:

```css
/* - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - */
```

Furthermore, the off-grid columns are grouped by their systems. If you only need one of the three systems (either one-fifth, one-seventh, or one-eighth), removing the other two systems is recommended to save on file size.


## Oh, Safari

You'll find that these grids don't line up wonderfully well in older versions of Safari. They're serviceable, but not perfect. This is due to how the browser rounds decimal places to pick a pixel value to display. The smaller that you're dividing your grid, the more noticeable this will be — for example, making a grid with twelve `one-twelfth` columns won't line up very well against a grid of two `one-half` columns.


Most of the time you're not going to be using grid columns that small, so it shouldn't be a problem. However, know that it's a known thing and there's nothing *Arrange* can do about it.