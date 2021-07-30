---
title: "Art"
---

> Art washes away from the soul the dust of everyday life.
> ~ Pablo Picasso

{{< rawhtml >}}

<script src="/js/lightgallery.min.js"></script>
<link type="text/css" rel="stylesheet" href="/css/lightgallery-bundle.min.css" />

<style>

.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-gap: 15px;
    padding: 15px;
    align-items: center;
}

.gallery a {
  overflow: hidden;
  position: relative;
  border: 2px solid hsl(202, 100%, 20%);
}

.gallery  a > img {

  -webkit-transition: -webkit-transform 0.15s ease 0s;
  -moz-transition: -moz-transform 0.15s ease 0s;
  -o-transition: -o-transform 0.15s ease 0s;
  transition: transform 0.15s ease 0s;
  -webkit-transform: scale3d(1, 1, 1);
  transform: scale3d(1, 1, 1);
  /* height: 100%; */
  width: 100%;
  /* object-fit: cover; */
}

.gallery  a:hover > img {
  -webkit-transform: scale3d(1.1, 1.1, 1.1);
  transform: scale3d(1.1, 1.1, 1.1);
}

</style>

Here are some of my oil, acrylic and watercolor paintings from 2010-2014.

<div id="lightGallery" class="gallery">
    <a href="/img/art/bear.jpg">
        <img src="/img/art/thumbs/thumb.bear.jpg">
    </a>
    <a href="/img/art/04.jpg">
        <img src="/img/art/thumbs/thumb.04.jpg">
    </a>
    <a href="/img/art/01.jpg">
        <img src="/img/art/thumbs/thumb.01.jpg">
    </a>
    <a href="/img/art/02.jpg">
        <img src="/img/art/thumbs/thumb.02.jpg">
    </a>
    <a href="/img/art/05.jpg">
        <img src="/img/art/thumbs/thumb.05.jpg">
    </a>
    <a href="/img/art/09.jpg">
        <img src="/img/art/thumbs/thumb.09.jpg">
    </a>
    <a href="/img/art/Harbour.jpg">
        <img src="/img/art/thumbs/thumb.Harbour.jpg">
        </li>
    <a href="/img/art/08.jpg">
        <img src="/img/art/thumbs/thumb.08.jpg">
    </a>
    <a href="/img/art/14.jpg">
        <img src="/img/art/thumbs/thumb.14.jpg">
    </a>
    <a href="/img/art/06.jpg">
        <img src="/img/art/thumbs/thumb.06.jpg">
    </a>
    <a href="/img/art/03.jpg">
        <img src="/img/art/thumbs/thumb.03.jpg">
    </a>
    <a href="/img/art/07.jpg">
        <img src="/img/art/thumbs/thumb.07.jpg">
    </a>
    <a href="/img/art/10.jpg">
        <img src="/img/art/thumbs/thumb.10.jpg">
    </a>
    <a href="/img/art/13.jpg">
        <img src="/img/art/thumbs/thumb.13.jpg">
    </a>
    <a href="/img/art/12.jpg">
        <img src="/img/art/thumbs/thumb.12.jpg">
    </a>
    <a href="/img/art/11.jpg">
        <img src="/img/art/thumbs/thumb.11.jpg">
    </a>
    <a href="/img/art/15.jpg">
        <img src="/img/art/thumbs/thumb.15.jpg">
    </a>
    <a href="/img/art/16.jpg">
        <img src="/img/art/thumbs/thumb.16.jpg">
    </a>
    <a href="/img/art/17.jpg">
        <img src="/img/art/thumbs/thumb.17.jpg">
    </a>
    <a href="/img/art/19.jpg">
        <img src="/img/art/thumbs/thumb.19.jpg">
    </a>
    <a href="/img/art/18.jpg">
        <img src="/img/art/thumbs/thumb.18.jpg">
    </a>
</div>  
<script>
    lightGallery(document.getElementById('lightGallery'), {
    speed: 0,
    });
</script>
{{< /rawhtml >}}
