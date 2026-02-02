# JabRef's blog

> This repository contains the source of the [JabRef blog](https://blog.jabref.org/).

Feel free to send blog entries.
Find details in our [CONTRIBUTING.md](CONTRIBUTING.md) file.

The layout is based on [Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy).
We use [Jekyll](https://jekyllrb.com/) as static site generator.
See [GitHub pages](https://pages.github.com/) for more details on the mechanics behind.

## Local Development

For local development, follow the [Jekyll installation instructions](https://jekyllrb.com/docs/installation/).
Installing the latest version of ruby followed by `gem install bundler` should be enough.

Afterward, run

```terminal
bundle install
jekyll serve --livereload
```

and go to <http://localhost:4000/> in your browser.

On Windows, using a dockerized environment is recommended:

```terminal
docker run -p 4000:4000 --rm --volume="C:\git-repositories\blog.jabref.org":/site bretfisher/jekyll-serve
```

In case you get errors regarding `Gemfile.lock`, just delete `Gemfile.lock` and rerun.

## Updating the theme

1. Update `Gemfile`
2. Update assets:
   1. `cd assets/lib`
   2. `git pull`
   3. `cd ../..`
3. git commit and PR creation
4. In case build fails because of missing assets, roll back the assets to the commit matching the release version of the theme.
