{% include _includes/nav.md %}

## CSS

We use  [Tailwind](https://v1.tailwindcss.com/docs/installation) for all css. Most of the time all CSS can be applied via the utility classes. If there is custom CSS that needs to be written, for example, something needs to have an exact width, a component HTML class and CSS file can be added.

```html
<section class="inline-block w-full py-20 mt-20 bg-white">
  <div class="o-container | bg-gray-5 text-center">

    <h2 class="text-style-21 text-gray-1">
      Heading
    </h2>

    <div class="description-classname | p-20 md:p-10 bg-gray-1">
      Content
      <span class="description-classname__child"></span>
    </div>

  </div>
</section>
```

```sass
// src/css/components/description-classname.css

.description-classname {
  width: 230px;
  height: 105px;

  @screen md {
  width: 200px;
  }
  
  // description-classname__child
  // Defined media queries inside children block
  &__child {
    height: 15px;

    @screen md {
    height: 20px;
    }
  }
  
  // BAD
  // @screen md {
  //   &__child {
  //     height: 20px;
  //   }
  // }
}
```