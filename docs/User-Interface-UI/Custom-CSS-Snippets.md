---
layout: default
title: Custom CSS Snippets
nav_order: 2
parent: User Interface (UI)
---
# **Custom CSS Snippets**
{: .no_toc }

---

<details open markdown="block">
  <summary>
    Table of Contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

**Custom CSS** allows you to modify Stash's stock style sheets.

The following is a list of some useful CSS snippets. You may use them by copying-and-pasting them into the Custom CSS editor found in the `Settings` > `Interface Configuration` panel or by navigating to `127.0.0.1:9999/settings?tab=interface`

Note: Future releases of Stash may break these CSS tweaks. CSS tweaks may not appear without flushing the Stash browser cache first on Chrome.

---

## Scenes

### Fit more thumbnails on each row

Reduce left and right padding on Scene and Performer grid pages allowing for more thumbnails on each row.

```css
/* [Scenes tab] Fit more thumbnails on each row */

.grid { padding: 0px !important; }
```

### Allow for longer string when displaying "Studio as Text" on scene thumbnails

```css
/* [Scenes tab] Allow for longer string when displaying "Studio as Text" on scene thumbnails */

.scene-studio-overlay {
	font-weight: 600 !important;
	opacity: 1 !important;
	width: 60% !important;
	text-overflow: ellipsis !important;
}
```

### Hide scene specs (resolution, duration) from scene card

```css
/* [Scenes tab] Hide scene specs (resolution, duration) from scene card */

.scene-specs-overlay {
  display: none;
}
```

### Hide studio logo/text from scene card

```css
/* [Scenes tab] Hide studio logo/text from scene card */

.scene-studio-overlay {
  display: none;
}
```
### Make the list of tags take up less width

```css
/* [Scenes tab] Make the list of tags take up less width */

.bs-popover-bottom {
  max-width: 500px
}
```

### Swap studio and resolution/duration positions

```css
/* [Scenes tab] Swap studio and resolution/duration positions */

.scene-studio-overlay {
  bottom: 1rem;
  right: 0.7rem;
  height: inherit;
  top: inherit;
}

.scene-specs-overlay {
  right: 0.7rem;
  top: 0.7rem;
  bottom: inherit;
}
```

### Adjust the mouse over behaviour in wall mode

```css
/* [Scenes tab] Adjust the mouse over behaviour in wall mode */

@media (min-width: 576px) {
 .wall-item:hover::before {
   opacity: 0;  
 }

 .wall-item:hover .wall-item-container {
   transform: scale(1.5);
 }
}
```

### Disable zoom on hover in wall mode

```css
/* [Scenes tab] Disable zoom on hover in wall mode */

.wall-item:hover .wall-item-container {
    transform: none;
}
.wall-item:before {
    opacity: 0 !important;
}
```

### Hide the scene scrubber

This will hide the large scene scrubber under the video player and max out the player's height.

![image](https://user-images.githubusercontent.com/66393006/121396473-1451a000-c95c-11eb-9467-61a2cc23378e.png)

```css
/* [Scenes tab] Hide the scene scrubber and max out the player's height */

.scrubber-wrapper {
  display: none;
}
```

### Hide the truncated text

This will hide the truncated text that appears under the tile and date.

```css
/* [Scenes Tab] - Hide the truncated text on scene card */

.TruncatedText.scene-card__description { 
   display: none;
}
```

---

## Performers

### Show entire performer image in performer card

```css
/* [Performers tab] Show entire performer image in performer card */

.performer.image {
  background-size: contain !important;
}
```

### Show a larger image in performer's page for desktop

```css
.performer-image-container{
  flex: 0 0 50%;
  max-width: 50%;
}
/* Changing .col-md-8 settings also affects studios and tags display. 50% should be good enough. */
.col-md-8 {
  flex: 0 0 50%;
  max-width: 50%;
}
```
### Show larger performer images in performers list

```css
/* original value: height: 30rem; min-width:13.25rem; */
.performer-card-image{
  height: 45rem;
  min-width: 20rem;
}
```

### Move the buttons in the Performer's edit panel to the top instead of bottom

```css
/* [Performers tab] Move the buttons in the Performer's edit panel to the top instead of bottom (in newer version of Stash, the buttons are already positioned both at top and bottom.  */

form#performer-edit {
    display: flex;
    flex-direction: column;
}
#performer-edit > .row {
    order: 1;
}
#performer-edit > .row:last-child {
    order: 0;
    margin-bottom: 1rem;
}
```

### Move the tags row in the Performer's edit panel to the second position (just after name)

```css
/* [Performers tab] Move the tags row in the Performer's edit panel to the second position (just after name).  */

form#performer-edit {
    display: flex;
    flex-direction: column;
}
#performer-edit > .row:nth-child(21) {
    order: -1;
}
#performer-edit > .row:first-child {
    order: -2;
}
```

---

## Galleries

### Grid view for galleries

```css
/* [Galleries tab] Grid view for galleries */

.col.col-sm-6.mx-auto.table .d-none.d-sm-block {
    display: none !important;
}
.col.col-sm-6.mx-auto.table .w-100.w-sm-auto {
    width: 175px !important;
    background-color: rgba(0, 0, 0, .45);
    box-shadow: 0 0 2px rgba(0, 0, 0, .35);
}
.col.col-sm-6.mx-auto.table tr {
    display: inline-table;
}
```

---

## Images

### Disable lightbox animation

```css
/* [Images tab] Disable lightbox animation */

.Lightbox-carousel {
  transition: none;
}
```

### Don't crop preview thumbnails

```css
/* [Images tab] Don't crop preview thumbnails */

.flexbin > * > img {
  object-fit: inherit;
  max-width: none;
  min-width: initial;
}
```

---

## Movies

### Better Movie layout for desktops

Making the front and back image much bigger. Left panel uses 70% while the right uses 30%.

#### Layout 1, regular size poster.

```css
/* [Movies tab] Better Movie layout for desktops: Regular size poster */

.movie-details.mb-3.col.col-xl-4.col-lg-6 {
  flex-basis: 70%
}
.col-xl-8.col-lg-6{
  flex-basis: 30% 
}
.movie-images{
  flex-wrap: wrap
}
.movie-image-container {
  flex: 0 0 500px
}
```
#### Layout 2, larger size poster.

```css
/* [Movies tab] Better Movie layout for desktops: Larger size poster */

.movie-details.mb-3.col.col-xl-4.col-lg-6 {
  flex-basis: 70%
}
.col-xl-8.col-lg-6{
  flex-basis: 30% 
}
.movie-images{
  flex-direction: column;
  flex-wrap: wrap
}
.movie-image-container {
  flex: 1 1 700px
}
```

---

## Global

### Change the order of navigation bar buttons

Use `order` values below 0 to move specific buttons to the left of the non-ordered buttons,  
and values above 1 to move them to the right of the non-ordered buttons.

**Before:**  
![image](https://user-images.githubusercontent.com/66393006/100487507-a35e3f80-3111-11eb-8cb5-a22738a50f12.png)  
**After:**  
![image](https://user-images.githubusercontent.com/66393006/100487468-6b56fc80-3111-11eb-817b-5f14f1d7b2f8.png)  

```css
/* [Global changes] Change the order of navigation bar buttons */

nav .navbar-nav:first-child {
  display: flex;
  flex-direction: row;
}
div.nav-link[data-rb-event-key="/tags"] {
  order: -2;
}
div.nav-link[data-rb-event-key="/movies"] {
  order: -1;
}
div.nav-link[data-rb-event-key="/scenes"] {
  order: 1;
}
```

### Hide the Donate button

```css
/* [Global changes] Hide the Donate button */

.btn-primary.btn.donate.minimal {
  display: none;
}
```

### Blur NSFW images

Use for when working on stash but don't want to expose NSFW images and text. May not be exhaustive:

```css
/* [Global changes] Blur NSFW images */

.scene-card-preview-video,
.scene-card-preview-image,
.image-card-preview-image,
.image-thumbnail,
.gallery-card-image,
.performer-card-image,
img.performer,
.movie-card-image,
.gallery .flexbin img,
.wall-item-media,
.scene-studio-overlay .image-thumbnail,
.image-card-preview-image,
#scene-details-container .text-input,
#scene-details-container .scene-header,
#scene-details-container .react-select__single-value,
.scene-details .pre,
#scene-tabs-tabpane-scene-file-info-panel span.col-8.text-truncate > a,
.gallery .flexbin img,
.movie-details .logo {
 filter: blur(8px);
}

.scene-card-video {
 filter: blur(13px);
}

.jw-video,
.jw-preview,
.jw-flag-floating,
.image-container,
.studio-logo,
.scene-cover {
 filter: blur(20px);
}

.movie-card .text-truncate,
.scene-card .card-section {
 filter: blur(4px);
}
```