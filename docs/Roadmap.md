---
layout: default
title: Roadmap
nav_order: 18
---
# **Roadmap**
<details open markdown="block">
  <summary>
    Table of Contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Any Time

Any of [the issues](https://github.com/stashapp/stash/issues) can be picked up by anyone at any time

## Near Term

### Logical Filters

Right now most filters are AND'ed, meaning that the result of multiple filters must meet all of the criteria to be shown.  We should support AND and OR for more flexibility.  The Database queries still need to be modified.

### Settings Screen improvements

The setting screen should support [configuring any FFMPEG option](https://github.com/stashapp/stash/issues/10).

### Watch later

Add a watch later boolean to scenes for scenes which you're interested in, but don't necessarily want to assign a rating to yet.

## Medium Term

### Collections

It would be nice to group scenes.  I've been thinking of a concept of a "Collection".  A collection would be a group of scenes / galleries.  There are times when web scenes have behind the scenes additions, collections would be a way to group those.

### JSON Schema

The exported JSON needs to be defined using the [JSON Schema Spec](https://json-schema.org/).  The spec should be generic enough that other apps could use it.  The schema should be used to validate any imported JSON.

Right now the schema uses the performer / studio image as the thing which is hashed as a unique identifier.  I'm unsure if it might be better to take the images out of the JSON...

### Multiple Performer Images

Adding multiple images for a performer seems like a good change.  Make them taggable so the user can configure what type of images they see when they see a performer card.  TBD how this would change the JSON schema.

## Long Term