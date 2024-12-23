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

Afterwards, run

```terminal
bundle install
jekyll serve --livereload
```

and go to <http://localhost:4000/> in your browser.

On Windows, using a dockerized environment is recommended:

```terminal
docker run -p 4000:4000 --rm --volume="C:\git-repositories\blog.jabref.org":/srv/jekyll jekyll/jekyll:4 jekyll serve
```

In case you get errors regarding `Gemfile.lock`, just delete `Gemfile.lock` and rerun.

Incremental building is also possible:

```terminal
docker run -p 4000:4000 --rm --volume="C:\git-repositories\blog.jabref.org":/srv/jekyll jekyll/jekyll:4 jekyll serve --incremental
```

## Updating the theme

1. Update `Gemfile`
2. Update assets:
   1. `cd assets/lib`
   2. `git pull`
   3. `cd ../..`
3. git commit and PR creation
4. In case build fails because of missing assets, roll back the assets to the commit matching the release version of the theme.

## Adding a blog entry for a new version

### Contributors list

See <https://blog.jabref.org/#december-18-2022-%E2%80%93-%F0%9F%8E%84-jabref-5-8-release-%F0%9F%8E%84> for an example for the list of contributors.

To get the list of contributors, use [github-contributors-list](https://github.com/koppor/github-contributors-list)

1. `jbang gcl@koppor/github-contributors-list --repository JabRef/jabref c:\git-repositories\jabref --startrevision=v5.13 --endrevision=v5.15 --filter=koppor,calixtus,Siedlerchr,tobiasdiez,but,k3KAW8Pnf7mkmdSMPHz27,HoussemNasri,apps/dependabot,apps/githubactions,ThiloteE,dependabot[bot],dependabot`
2. Copy and paste the Markdown
3. Preview
4. Double check with <https://github.com/JabRef/jabref/graphs/contributors?from=2023-09-02&to=2023-10-22&type=c>
5. Double check with merged PRs: <https://github.com/JabRef/jabref/pulls?q=is%3Apr+sort%3Aupdated-desc+is%3Amerged>. On 2023-10-22 (when the JavaScript-variant was used), contributors with PRs being merged on the release date did not show up. Example: <https://github.com/JabRef/jabref/pull/10497>
