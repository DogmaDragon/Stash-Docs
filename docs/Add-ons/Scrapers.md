---
layout: default
title: Scrapers
nav_order: 1
has_children: false
parent: Add-ons
---
# Scrapers
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

## Scrapers
Scrapers are the way to retrieve information from websites for your movies/scenes/galleries/performers...etc. Using scrapers wisely, you can avoid typing information manually and repetitively. They can help you quickly establish links between movies/scenes and performers/studios, add relative tags, then download covers/posters for easy recognition. It's a great feature to organize your video or image collections.<br>
All scrapers are ".yml" files. Some scrapers like script scrapers also come with their own ".py" files or ".js" files.

### Installation
To install a scraper:
  1) Make sure you have the "scrapers" folder in the same location of your Stash app. If you don't have it, create that folder/directory. You can also specify the name of this folder in the config.yml.
  2) Go to the [community scrapers repo](https://github.com/stashapp/CommunityScrapers){:target="_blank"} and download the scraper you want. Read the [scrapers list](https://github.com/stashapp/CommunityScrapers/blob/master/SCRAPERS-LIST.md){:target="_blank"} and make sure which one to download. All scrapers are in .yml format. Some of them requires Python, if you use those, you need to install Python in your machine, and don't forget to get the corresponding .py file as well.
<br>Note: For Python scrapers, it's also helpful to read the .py file. Some of them require extra python components installed to work.
  3) Once the new scrapers are in position, you need to go to "Settings->Scraping" and click on "Reload Scrapers" button. You should see your scrapers listed in the list below that button.
  4) Navigate to the scene/gallery/movie/performer you want to scrape.
* If that's a URL scraper, you need to paste the URL in its "URL" blanket, and the scrape icon next to it should light up.
* If that's a Search-By-Name scraper, you can provide the name and choose "Scrape With...", and the scraper should fetch the list of potential matches for you.
5) You will preview the scrape result before you commit the change. Check on the left will keep the original value, check on the right will make the change.

---

## Scraper Types

### By Searching Type
- **Fragment**<br>
This kind of scrapers will fetch the metadata from a website, by using existing data from Stash, like a scene's file name, performer's name...etc. Fragment scrapers will get all the data Stash knows about that scene/performer/gallery, so it's quite flexible when fetching information.<br>
Scrapers includes: AdultTimeAPI.yml, JavLibrary.yml, ThePornDB.yml
- **Search By Name**<br>
A Search-By-Name scraper will get only "name" input from a scene or performer, then it will search a website with that name, and return a list of results.<br>
Scrapers includes: Babepedia.yml, FreeonesCommunity.yml, IAFD.yml
- **Search By URL**<br>
Most scrapers fetch metadata from a given URL, either by using XPath, JSON, or scripts. For this kind of scrapers you need to know the URL for that scene/performer/gallery/movie so they can extract information from it.<br>
Scrapers includes: All other scrapers.

### By Implementation
- **XPath and JSON Scrapers**<br>
This is the most common type of scrapers, which use either XPath parser to pin-point the information and retrieve them, or send out JSON requests to get the information. xpathScraper and jsonScraper can be mixed in the same .yml file.
- **CDP Scrapers**<br>
This type of scrapers is mostly the same as XPath/JSON scrapers, except it will launch a headless Chrome browser to retrieve the information from websites. It can also get cookies, simulate a mouse click and other actions. These scrapers have `useCDP: true` setting in them.
- **Python / Javascript Scrapers**<br>
This type of scrapers will launch python or javascripts to retrieve information from websites. Script scrapers are powerful, versatile and cross-platform. So they usually can do much more than regular scrapers. To install this kind of scrapers, you need to copy not only the .yml file, but also all the script files like .py or .js that associated with it.

---

## More Details
You can view the [detail information about scrapers here](https://github.com/stashapp/stash/blob/develop/ui/v2.5/src/docs/en/Scraping.md){:target="_blank"} or [Community Scrapers Readme here](https://github.com/stashapp/CommunityScrapers){:target="_blank"}.

---

## Create your own.
To create your own scraper, there is [detail information about that as well](https://github.com/stashapp/stash/blob/develop/ui/v2.5/src/docs/en/ScraperDevelopment.md){:target="_blank"}. Best way to start is to read the simple ones and understand how xpath works. The [XPath Cheetsheet](https://devhints.io/xpath){:target="_blank"} is quite useful in creating a yml file. In Firefox you can use xpath search in "Web Developer Tools (F12)". The "search HTML" bar actually accepts xpath searches. You can use it to verify your xpath queries.

---

## Contribution
The Scraper community always welcome new members. If you create a nice scraper and find it stable and useful, you can share it via [the GitHub repo](https://github.com/stashapp/CommunityScrapers){:target="_blank"}. Create a pull request, and let the mod review your work. The mods are busy, so it will probably take a few days, or a couple of weeks, but it will be a great feeling once your contribution is accepted by the community.