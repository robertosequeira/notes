# Bootstrap 4

## Layout

* Containers

  ```
  div.container
  div.container-fluid
  ```

* Breakpoints 

  ```
  xs
  sm
  md
  lg
  xl
  ```

* Columns
  
  ```
  /** Equal width **/

  // all breakpoints
  div.container
    div.row
      div.col
      div.col

  div.container
    div.row
      div.col-[breakpoint]
      div.col-[breakpoint]
  
  // multirow
  div.container
    div.row
      div.col
      div.col
      div.w-100
      div.col
      div.col

  /** Explicit width **/

  // all breakpoints
  div.container
    div.row
      div.col-[number]
      div.col-[number]

  div.container
    div.row
      div.col
      div.col-[number]
      div.col

  div.container
    div.row
      div.col-[breakpoint]-[number]
      div.col-[breakpoint]-[number]  
  ```

* Alignment

  ```
  /** Vertical **/

  div.container
    div.row.align-items-start
      div.col
  
  div.container
    div.row.align-items-center
      div.col

  div.container
    div.row.align-items-end
      div.col

  div.container
    div.row
      div.col.align-self-start
      div.col.align-self-center
      div.col.align-self-end

  /** Horizontal **/

  div.container
    div.row.justify-content-start
      div.col-4
      div.col-4

  div.container
    div.row.justify-content-center
      div.col-4
      div.col-4
  
  div.container
    div.row.justify-content-end
      div.col-4
      div.col-4
  
  div.container
    div.row.justify-content-around
      div.col-4
      div.col-4

  div.container
    div.row.justify-content-between
      div.col-4
      div.col-4
  ```

* No gutters

  ```
  div.container
    div.row.no-gutter
      div.col
      div.col
  ```

* Column breaks

  ```
    div.container
      div.row
        div.col
        div.w-100
        div.col
    
    // break only at md and up
    div.container
      div.row
        div.col
        w-100.d-none.d-md-block
        div.col
  ```

* Order

  ```
  div.row
    .col.order-[number]
    .col.order-[breakpoint]-[number]
    .col.order-first
    .col.order-last
  ```

* Offset

  ```
  // offset
  div.row
    div.col-[breakpoint]-[number].offset-[breakpoint]-[number]
  
  // margin left/rigth
  div.row
    div.col-2
    div.col-2.ml-auto
  
  div.row
    div.col-2.mr-auto
    div.col-2
  
  div.row
    div.col-2
    div.ml-[breakpoint]-auto
  ```

## Colors

  ```
  primary
  secondary
  success
  danger
  warning
  info
  light
  dark
  white

  .text-[color]
  .bg-[color]
  .bg-gradient-[color]
  ```

## Utilities

* Borders

  ```
  // add
  span.border
  span.border-top
  span.border-right
  span.border-bottom
  span.border-left

  // remove
  span.border-0
  span.border-top-0
  span.border-right-0
  span.border-bottom-0
  span.border-left-0

  //color
  span.border.border-[color]

  //radius
  rounded
  rounded-top
  rounded-right
  rounded-bottom
  rounded-left
  rounded-circle
  rounded-0
  ```

* Clearfix

  ```
  div.clearfix
    button.btn.btn-secondary.float-left
    button.btn.btn-secondary.float-right
  ```
* Display

  ```
  none
  inline
  inline-block
  block
  table
  table-cell
  table-row
  flex
  inline-flex

  .d-[value]
  .d-[breakpoint]-[value]
  ```

* Float

  ```
  .float-left
  .float-right
  .float-none

  .float-[breakpoint]-left
  .float-[breakpoint]-right
  .float-[breakpoint]-none
  ```
* Position

  ```
  .position-static 
  .position-relative
  .position-absolute
  .position-fixed
  .position-sticky
  
  .fixed-top
  .fixed-bottom
  
  .sticky-top
  ```

* Sizing

  ```
  // width
  w-25
  w-50
  w-75
  w-100

  // height
  h-25
  h-50
  h-75
  h-100

  // max-width/max-height
  mw-100
  mh-100
  ```

* Spacing

  ```
  // size
  0
  1
  2
  3
  4
  5
  auto

  // sides
  t - top
  r - right
  l - left
  b - bottom
  x - left and right
  y - top and bottom

  // margin
  m-[size]
  m[sides]-[size]
  m[sides]-[breakpoint]-[size]

  // padding
  p-[size]
  p[sides]-[size]
  p[sides]-[breakpoint]-[size]

  // horizontal centering
  div.mx-auto
  ```

* Text

  ```
  .text-left
  .text-center
  .text-right

  .text-[breakpoint]-left
  .text-[breakpoint]-center
  .text-[breakpoint]-right

  .text-nowrap
  .text-truncate

  .text-lowercase
  .text-uppercase
  .text-capitalize

  .font-weight-bold
  .font-weight-normal
  .font-weight-light
  .font-italic
  ```

* Vertical alignment

  ```
  .align-baseline
  .align-top
  .align-middle
  .align-bottom
  .align-text-top
  .align-text-bottom
  ```

* Visibility

  ```
  .visible
  .invisible
  ```
