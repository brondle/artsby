![The artsby logo in comic sans](static/img/header.png)
# Artsby

### [Demo Site](https://brondle.github.io/artsby_demo/). 

<img src='static/img/demo_site.png' width='400px'><img src='static/img/work.png' width='400px'><img src='static/img/about.png' width='400px'>


Artsby is a [Gatsby](https://www.gatsbyjs.com/) framework for digital art exhibits (it generates static sites, so it’s ideal for static artworks, [p5.js](https://p5js.org/) sketches or anything without a server).

Hosting a bunch of different digital artworks in a single place, with a coherent aesthetic, is a huge hassle. This takes the hassle out of the equation by keeping them all isolated in their own folders and putting them into the noble and oft-maligned iframe for you or your audience’s viewing pleasure, creating a simple digital gallery. Just plug in their work, fill out a couple JSON files, and you’ve got an exhibit, an about page, and you’re ready to go.

You could probably also adapt this for a portfolio or something, I don’t know, I’m not in charge of you.


This is based on a framework I built for the [generative unfoldings](https://generative-unfoldings.mit.edu/) exhibit at MIT, so you can also make pretty things like this. 

<img src='static/img/gen_unfo.png' width='600px'>

It’s a bit messy and there’s some code in there that’s not being used but may be useful to you (like hiding the header). At any rate, I thought I’d put it out there in the hopes it’s useful to someone.


## Setup

There’s some demo content in here that you’ll want to remove for your own work: just clear out `src/works` and `static/works`.

Clone the repo and run `npm install`.

In `static/works`, put folders containing your digital artworks. **There must be an index.html at the root of each folder**, which will be what displays when the site builds.

In `static/data`, put your exhibit info in `about.json`, and each artist’s info in `work_info.json`. These can all hold HTML as well as regular strings, so go wild with it. These JSON files auto-populate each page with your exhibit and work details.

#### Sample About
```
{
  "about_title": "My Cool Art Exhibition",
  "about_text": "This is my cool art exhibition. Check it out!",
  "header_image": "img/header.png"
}
```

#### Sample Artist Info
```
{
  "works": [{
    "url": "rectangles", // this should be the same as the folder name in static/works
    "name": "Rectangles",
    "altText": "A large number of multi-colored rectangles layered over each other.", //alt text for the homepage image
    "artist": "Brent Bailey",
    "bio": "Brent Bailey made this boilerplate."
  }]
}
```



In `static/img`, for the homepage, you can put images of each artwork titled with the same name as the artwork’s folder in `static/works`, and it’ll auto-populate the homepage with them. You can add your own header image in there, whatever you want.

Once everything’s set up, run `bash setup.sh` - this just copies the index.html files from the works to the src folder, because I haven’t found a less dumb way to get this to work.

#### Bing bang boom - you’ve got an art exhibit! 

You’ll have to run `gatsby build` once to get everything in the right place, but then you can play around with it -

Run `gatsby develop` to get your development site running on `localhost:8000`, and `gatsby build` to create the final version when you’re satisfied - you can test the built version on `localhost:9000` by running `gatsby serve`. 

You can change the styles to your liking in `src/styles.scss`, and if you’re comfortable with Gatsby/React, this is a pretty minimal build that you can add to.

You might want to set your [site metadata](https://www.gatsbyjs.com/docs/add-page-metadata/) in gatsby-config if you care about things like SEO.

By default, all filepaths just point to root. If you’re deploying to GitHub Pages, you’ll [want to set your path prefix](https://www.gatsbyjs.com/docs/how-to/previews-deploys-hosting/how-gatsby-works-with-github-pages/) in `gatsby-config.js` and make sure you’re prefixing your paths when you build, but if you use FTP or something simple you should be fine!

## Known Bugs

If you’re working with p5 and relying on windowWidth, the fullscreen button won’t automatically change your sketch width - you’ll have to use a windowResized() function like the starter code.
