# Sass

## Variables
```scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
    font: 100% $font-stack
    color: $primary-color;
}
```

## Nesting
```scss
nav {
    ul {
        margin: 0;
        padding: 0;
        list-style: none;
    }

    li { display: inline-block; }

    a {
        display: block;
        padding: 6px 12px;
        text-decoration: none;
    }
}
```

## Modules
```scss
// _base.scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
    font: 100% $font-stack
    color: $primary-color;
}
```
```scss
// styles.scss
@use 'base';

$font-stack: Helvetica, sans-serif;
$primary-color: #333;

.inverse {
    background-color: base.$primary-color;
    color: white;
}
```

## Mixins & Functions
```scss
@mixin transform($property) {
    -webkit-transform: $property;
    -ms-transform: $property;
    transform: $property;
}

.box { @include transform(rotate(30deg)); }
```

## Inheritance
```scss
$toast-message {
    border: 1px solid #ccc;
    padding: 10px;
    color: #333;
}

.message {
    @extend $toast-message;
}

.success {
    @extend $toast-message;
    border-color: green;
}

.error {
    @extend $toast-message;s
    border-color: red;
}

.warning {
    @extend $toast-message;
    border-color: yellow;
}
```

## Conditionals
```scss
@mixin triangle($size, $color, $direction) {
    height: 0;
    width: 0;

    border-color: transparent;
    border-style: solid;
    border-width: $size / 2;

    if $direction == up {
        border-bottom-color: $color;
    } @else if $direction == right {
        border-left-color: $color;
    } @else if $direction == down {
        border-top-color: $color;
    } @else if $direction == left {
        border-right-color: $color;
    } @else {
        @error "unknown direction #{direction}."
    }

    .next {
        @include triangle(5px, black , right)
    }
}
```