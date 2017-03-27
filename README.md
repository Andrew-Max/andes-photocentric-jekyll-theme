# andes-photocentric
A Jekyll theme where photos are the content, and text is secondary.

## Dependencies

### Ruby and Ruby Gems
 Can be installed with RVM. Instructions at: https://rvm.io/rvm/install

### Gems Needed
 First manually install bundler with `gem install bundler`
 Then `bundle install` to resolve the rest of the gem dependencies listed in the `Gemfile`

## Running the app

After all the dependencies are met, just run `$ jekyll serve` to run the app.
It should be available in the browser by typing `localhost:4000` into the url bar

## Creating New Posts
To create a new post, add a new file to the `_posts` directory with a title in the format
`YEAR-MONTH-DAY-title.MARKUP`
for example `2012-09-12-how-to-write-a-blog.md`

### Inside the new post file
There are two major parts to a post: front-matter and content

#### Front matter
Front matter is metadata that is required by Jekyll and this theme to compose the blog.

It should be in the format:
```
---
layout: post - literally the word `post`
title:  make a title
date:   date from the file name
s3-base: url of the bucket of your photos  for example
preview: location of a photo in the bucket at s3-base
previousurl: you can link to the previous article here
nexturl: you can link to the next article here
images:
  - type: horizontal
    id: 1
  - type: vertical
    id: 1
  - type: pano
    id: 1
---
```

Note that the front matter must start and end with ```

The images asssume an amazon s3 bucket with a specific directory structure

Each Bucket should contain two subdirectories
`full` - the large photos that get displayed when you click on a photo
`thumb` - the thumbs that get displayed on the photo wall
also at this level should be an image called `cover.jpg` which will be the preview image for this album

In both `full` and `thumb` there should be three subdirectories:
`horizontal`
`vertical`
`pano`
Inside of these directories should be numbered photos starting at 1 ie `1.jpg`

so in the images section
```
  - type: horizontal
    id: 1
```
on the photo wall routes to s3-base/thumb/horizontal/1.jpg

and when you click on that photo, the link will be to s3-base/full/horizontal/1.jpg


## Installation

Add this line to your Jekyll site's Gemfile:

```ruby
gem "andes-photocentric-jekyll-theme"
```

And add this line to your Jekyll site's `_config.yml`:

```yaml
theme: andes-photocentric-jekyll-theme
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install andes-photocentric-jekyll-theme

## Usage

TODO: Write usage instructions here. Describe your available layouts, includes, and/or sass.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/andrew-max/andes-photocentric-jekyll-theme. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## Development

To set up your environment to develop this theme, run `bundle install`.

Your theme is setup just like a normal Jekyll site! To test your theme, run `bundle exec jekyll serve` and open your browser at `http://localhost:4000`. This starts a Jekyll server using your theme. Add pages, documents, data, etc. like normal to test your theme's contents. As you make modifications to your theme and to your content, your site will regenerate and you should see the changes in the browser after a refresh, just like normal.

When your theme is released, only the files in `_layouts`, `_includes`, and `_sass` tracked with Git will be released.

## License

The theme is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

