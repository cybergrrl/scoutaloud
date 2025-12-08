+++
title = """About this project"""
template = "xmas-movie-about.html"
+++

## About this application

This is an ongoing project to help you discover new interesting Christmas movies. 

To build the database, I used many user-lists from [Letterboxd.com](https://letterboxd.com). I made an effort to only include high-quality lists that contain actual Christmas . As a Christmas film, I count any film that fulfils any of the following criteria:

- it is about Christmas directly (for example *A Christmas Carol*) or
- it plays out entirely or mostly over the Christmasor mostly over the Christmasor mostly over the Christmas season (for example *Die Hard*) or
- pivotal scenes of the film are set at Christmas (for example *Little Women*)

Just having a random scene with a Christmas tree or a Santa in the background is not enough. Having a Christmas release date is also not enough. And being a popular watch over the holiday season definitely does not count (good-bye *Harry Potter* films).

## Attribution

The information displayed for each film has been taken from [Letterboxd.com](https://letterboxd.com) (text content); the film posters come directly from [TMDB](https://www.themoviedb.org/). 

<div class="tmdb-attribution">

![TMDB Logo](/projects/xmas-movie-discovery/TMDB-logo.svg)

*To obtain the posters, the TMDB API was used but this site is not endorsed, certified, or otherwise approved by TMDB.*

</div>

I would like to thank all the folks over on Letterboxd who created Christmas movie lists.
I would also like to thank the owners of the following two github repositories as well as the other contributors - their code enabled me to scrape the lists of Christmas movies to build my database: [L-Dot](https://github.com/L-Dot/Letterboxd-list-scraper) and [cjpeterson](https://github.com/cjpeterson/Letterboxd-list-scraper/tree/master).

Thanks also to [Toby](https://codepen.io/tobyj) on codepen who created the [twinkling christmas lights](https://codepen.io/tobyj/pen/QjvEex) on which i based my own adapted lights.

## How I built the app

To build the database, I first identified many Christmas movie lists on Letterboxd. 
I used the scripts mentioned above to scrape those lists. 
I had to edit the scripts a bit too because I needed specific information moving forward, for example to get the link to TMDB.
Then i wrote a number of Python scripts to enrich the data further: 
- I added more genres (no Christmas move genre list is complete without "Hallmark" or "A Christmas Carol", right?)
- I added a movie poster link (by use of the TMDB API)
And finally, I used a Python script to create all the film pages for my app.
