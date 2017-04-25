footer: @nateberkopec of www.speedshop.co for @heroku

---

# Hello! Please:
## Download Chrome Canary
## ...and Have a local Rails app w/a decently complex frontend running

---

# Front end
# performance
# for full-stack
# developers

---

![fit](speedshop_s.png)

---

![fit](blog.png)

---

![fit](nate_perf_explanation.gif)

---

![fit](persons.png)

---

![fit](lang.png)

---

![fit](loading.gif)

---

# [fit] Chrome DevTools

---

# [fit] Assumptions

---

# [fit] Using Canary

---

# [fit] Turn on Chrome DevTools experiments
# [fit] `chrome://flags/`

---

# [fit] Turn off any extensions

---

# [fit] Load times

---

# [fit] The Thin Orange Line

> First Meaningful Paint is essentially the paint after which the biggest above-the-fold layout change has happened, and web fonts have loaded.

---

# [fit] 1000 milliseconds

---

# [fit] 100 milliseconds from input

---

# [fit] Network speeds

* US: ~25% of users still on 3G
* US: ~1.4 Megabytes/Second
* Worldwide: ~625 KB/s

---

# Average page is 2.5 MB

---

# [fit] Load performance is
## (mostly) 
# [fit] network performance

---

# [fit] Critical rendering path

---

1. Get HTML document
2. Start speculative preloading
3. Build DOM and CSSOM
4. Combine into render tree
5. Layout 
5. Paint

---

# [fit] Javascript is the enemy

---

1. Wait for script to download
2. If all the CSS on this page hasn't downloaded yet, wait again.
3. Parse and execute this script

---

![fit](jstransfersize.png)

---

# [fit] Not just gzipped size

---

# [fit] 1MB ~= 1 sec *just to parse*

---

![fit](parsetimecomparo.jpeg)

---

![fit](parsetime.png)

---

# Exercise 1: Let's Look at the CRP of a Page

---

[Discourse](https://try.discourse.org)

---

# How to Halve Load Times With One Weird Trick:
# No Javascript

---

# `async`

---

# `defer`

---

# Last resort
# Bottom of the page

---

# Making JS smaller

* Webpack
* Google's Closure Compiler
* Using smaller libraries

---

# Exercise 2: Identifying JS Blocking

---

# [Coderwall](http://coderwall.com)

---

# [OpenStreetMap](http:/openstreetmap.org)

---

# [fit] Inlining CSS

---

# [fit] CSS in the body

---

[Demo](https://jakearchibald-demos.herokuapp.com/progressive-css/)

---

![fit](csssize.png)

---

# Exercise 3: Looking for blocking CSS

---

# [HN](https://news.ycombinator.com/)

---

# [fit] HTTP/2 

---

# [fit] Parallelizing many resources

---

# [Sidekiq.org](http://sidekiq.org)

---

# [fit] Server push

---

# Link headers

```Link: </css/style.css>; rel=preload;```

---

1. application.js and application.css
2. Things which cannot be cached
3. Next pages 
4. Redirects

---

# [rack\_http\_preload](https://github.com/nateberkopec/rack_http_preload)


---

# [fit] Streaming responses 

---

# [fit] Doesn't actually work (lol)

---

# [fit] Webfonts

---

![fit](webfonts.png)

---

![fit](fontsize.png)

---

# [Basecamp](https://basecamp.com)

---

# [Rubygems.org](https://rubygems.org)

---

* Use Webfonts as spice, not filler.
* Don't use Typekit (blocking JS)
* Just use Google WebFonts

---

# [fit] HTTP Caching

---

### `$(document).ready();`

---

# [fit] Big DOMs

---

![fit](domsize.png)

---

# [fit] Image optimization

---

1. Find blocking JavaScript
2. Find blocking CSS and WebFonts
4. Optimize images
5. Add server push and/or HTTP/2
6. Analyze startup performance (document.ready)
7. Check HTTP caching
