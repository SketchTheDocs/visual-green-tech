# Under The Hood

This website is built using the [Hugo](https://gohugo.io) static site generator and hosted at the [GitHub Pages endpoint](http://sketchthedocs.dev/visual-green-tech) for this repo. I used the [Quickstart](https://gohugo.io/getting-started/quick-start/) guide to get started and chose the [Newsroom theme](https://github.com/onweru/newsroom) for this purpose.

Here are the steps followed:

---

`STEP 1`:  install hugo for development.

```
$ brew install hugo
$ hugo version
hugo v0.83.0+extended darwin/amd64 BuildDate=unknown
```
---

`STEP 2`: Create a new hugo project (source directory)

```
$ hugo new site www
```

---


`STEP 3`: Add A Theme

Follow [theme directions](https://gohugo.io/getting-started/quick-start/#step-3-add-a-theme) - you should be able to substitute [a different theme](https://themes.gohugo.io/) and use the same process.

```
$ cd www
$ git submodule add https://github.com/onweru/newsroom.git themes/newsroom
```

Themes I've liked: <br/>
[Ananke](https://github.com/budparr/gohugo-theme-ananke.git), [Stack](https://github.com/CaiJimmy/hugo-theme-stack), [Tranquilpeak](https://github.com/kakawait/hugo-tranquilpeak-theme.git), [Frances](https://github.com/mcrwfrd/hugo-frances-theme.git), [Coder](https://github.com/luizdepra/hugo-coder.git), [Newsroom](https://github.com/onweru/newsroom)

---

`STEP 4`: Customize Theme

First, edit the `www/config.toml` to specify the theme used

```
baseURL = "https://sketchnotes.dev/visual-green-tech/"
languageCode = "en-us"
title = "Visual Green Tech"
theme = "newsroom"
```

Then, look at that theme's download/homepage for information on customization options and update the `www/config.toml` accordingly. For example [this](https://github.com/onweru/newsroom#configuration) is the configuration guide for Newsroom and [this](https://github.com/onweru/newsroom/tree/master/exampleSite) is a sample from the exampleSite. 


---

`STEP 5`: Test your website presentation locally

This supports hot reload so you can see the impact of configuration and content changes to your websitee as you make them. The "-D" option indicates draft mode (allowing you to see posts still in draft state)

```
$ cd www/
$ hugo server -D
..
..
Web Server is available at http://localhost:1313/visual-green-tech/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

---
`STEP 6`: BUILD FOR DEPLOYMENT

The default build directory is local.
Followed this [guidance](https://gohugo.io/getting-started/quick-start/) I updated my `www/config.toml` to specify a custom _publishdir_ ("docs") as the target.

Now just build the static website from this source using this command:

```
$ cd www/
$ hugo -D
```
 
`Note`: Go into the GitHub Settings for gh-pages and point it to the "docs/" folder. You static website is now automatically hosted at the GitHub Pages endpoint for this repo.



## Maintenance

Simply add content into the relevant subfolders using something of the form below, where `xxxxx` is a slug that is unique to the site.

```
$ hugo new posts/xxxxx.md
```

This generates a new file under the `content/posts` directory. If your local server was running, the changes should show up instantly in the browser (hot reload).

The _newsroom_ theme assumes `static/images` to be the root for loading images. Anything placed in this directory can be accessed by its name (or relative sub-path from this root)

To build/deploy, the current process is manual. Simply run the command below to get the `docs/` target directory updated. Then commit the changes to GitHub, which will auto-refresh the static GH Pages deployment endpoint.

```
$ cd www/
$ hugo -D
```

`TODO:` Automate this step with GitHub Actions.
