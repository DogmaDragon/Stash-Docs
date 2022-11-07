---
layout: default
title: Add-ons
nav_order: 4
has_children: true
has_toc: false
---
# **Add-ons**
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

# Third-Party Plugins
Stash plugins add further features that Stash doesn't itself provide.  There are also several [officially hosted plugins and scripts](https://github.com/stashapp/CommunityScripts/blob/main/PLUGINS-LIST.md) available via the CommunityScripts repository. This document contains a list of plugins and scripts created by users and contributors.

To install a plugin, save them to `%USERPROFILE%\.stash\plugins` on Windows or `/root/.stash/plugins` on Unix systems (Mac, Linux, etc.). The `plugins` directory won't exist by default so you will have to create it. Once installed, go to the Plugins page in your Stash settings and reload plugins.

**Note: these plugins are created by third parties and not officially affiliated or supported by the core Stash team.  If you have issues, please reach out to the original creators.**

### List of Plugins

Category | Plugin | Author | Description
-|-|-|-
Downloader | [YT-DL Downloader](https://github.com/niemands/StashPlugins) | niemands | Download Videos automated with yt-dl and add the scrape tag for Bulk URL Scraper |
Images | [Gallery Tags](https://github.com/niemands/StashPlugins) | niemands | Copy information from attached scene to galleries   |
Images | [Update Image Titles](https://github.com/niemands/StashPlugins) | niemands | Update all image titles (Fixes natural sort)        |
Maintenance | [Duplicate Finder](https://github.com/WithoutPants/stash-plugin-duplicate-finder) | WithoutPants | Detects and marks duplicate scenes within Stash
Metadata | [Performer Creator](https://github.com/com1234475/stash-plugin-performer-creator) | com1234475 | Creates performers from scenes based on filenames.
Metadata | [Set PH Urls](https://github.com/niemands/StashPlugins) | niemands | Add urls to pornhub scenes downloaded by Youtube-dl |
Scraping | [Bulk URL Scraper](https://github.com/niemands/StashPlugins) | niemands | Bulk scene url scraping                             |
Scraping | [OnlyFans Scraper](https://github.com/ALonelyJuicebox/OFMetadataToStash) | ALonelyJuicebox | Scrape scene and performer info from OnlyFans 
Scraping | [Scrape with](https://github.com/Tweeticoats/stash-plugin-scrape_with)|Tweeticoats | Batch scrape scenes and performers. For example tag a scene with scrape_with_xbvr and run the task to run that scraper. Run artist scrapers on all performers missing a url. Run the performer image scraper on all performers.
VR | [stash-deovr](https://github.com/Tweeticoats/stash-deovr) | Tweeticoats | Create an index json file /deovr used by the vr player allowing you to use DeoVR to play 2d and 3d videos from stash.

# Scripts
Scripts are standalone programs that can interact with stash either through graphql queries or by directly editing stash's database/files.

To install a script follow the script's install instructions.

### List of scripts

Category | Script | Author | Description
-|-|-|-
Maintenance | [SQLITE Renamer for Stash](https://github.com/Belleyy/Stash-Renamer-Python) | Belley  | Renames your files using stash's metadata

# Third-Party Integrations
Integrations are repositories developed to integrate Stash into other programs.

Category | Name | Author | Description
-|-|-|-
Kodi | [plugin.video.stash](https://github.com/gitgiggety/plugin.video.stash) | gitgiggety | plugin.video.stash is an add-on for the Kodi home theater center software to incorporate Stash, an organizer for your porn

# Utilities

Other external applications that utilise or interact with stash in some way.

Category | Name | Author | Description
-|-|-|-
Companion | [Stash_helper](https://github.com/philpw99/Stash_Helper) | philpw99 | Adds some windows-specific tools to Stash (navigate from icon, installation help, etc)
VR | [stash-vr](https://github.com/o-fl0w/stash-vr) | o-fl0w | Watch your stash library in VR.
VR | [stash-vr-companion](https://github.com/Tweeticoats/stash-vr-companion) | Tweeticoats  | Similar to stash-deovr as above but designed as a web app that sits in a docker container next to stash to make it easier to use and add more functionality.
