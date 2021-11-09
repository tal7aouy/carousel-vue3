# Vue3 Carousel

A reusable Carousel build using Vue3 and composition Api.

## How to Make it reusable

Go to `views\Home.vue` then ⬇️

you can make the carousel reusable using change the `props` below :

```html
<Carousel
  :navigation="true"
  :pagination="false"
  :startAutoPlay="true"
  :timeDuration="2000"
  class="carousel"
  v-slot="{ currentSlide }"
>
  ...
</Carousel>
```

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```
