###Indentation
***

Indent every child element, not including children like `<i>` and `<span`>, which are semantically inline. Pretty straight forward.

```html

// good
<div>
  <p>Text</p>
</div>

// bad
<div>
<p>Text</p>
</div>
```

A larger example....

```html

// good
<header>
  <div class="nav-center">

    <a href="/">
      <img class="primary-logo" src="/someimage.png">
    </a>

    <nav>
      <div class="nav-item">
        <a class="dropdown" href="/route"><i class="fa fa-database"></i> Route</a>
      </div>
      <div class="nav-item">
        <a href="/source" target="_blank"><i class="fa fa-git-square"></i> Source Code</a>
      </div>
    </nav>

    <div class="button-group">
      <a href="/route1"><i class="fa fa-plus"></i> Route 1</a>
      <a href="/route2"><i class="fa fa-plus"></i> Route 2</a>
      <a href="/route3"><i class="fa fa-plus"></i> Route 3</a>
    </div>
    
  </div>
</header>

// bad
<header>
  <div class="nav-center">

    <a href="/">
    <img class="primary-logo" src="/someimage.png">
    </a>

    <nav>
    <div class="nav-item">
    <a class="dropdown" href="/route"><i class="fa fa-database"></i> Route</a>
    </div>
    <div class="nav-item">
    <a href="/source" target="_blank"><i class="fa fa-git-square"></i> Source Code</a>
    </div>
    </nav>

    <div class="button-group">
    <a href="/route1"><i class="fa fa-plus"></i> Route 1</a>
    <a href="/route2"><i class="fa fa-plus"></i> Route 2</a>
    <a href="/route3"><i class="fa fa-plus"></i> Route 3</a>
    </div>
    
  </div>
</header>
```
