This is the source code behind http://pensieve.swijaya.com/.

# Building Pensieve

Powered by [Jekyll](https://jekyllrb.com/) with
[Minimal Mistake](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
plugin/theme.

This repository also contains a `.devcontainer` folder with a `Dockerfile`
and `devcontainer.json` files. The former builds a container with Jekyll and its
Ruby dependencies ready to use. The latter describes a remote VS Code
development environment that I use with GitHub Codespaces.

Once you've set up the build environment, whether locally or remotely in
Codespaces, build the site with:

```sh
$ bundle install && rake
```

The generated static files will be located in the `_sites` folder.

To interact with the pages during development, run the following command:

```sh
$ rake serve
```

And then open your browser and navigate to http://127.0.0.1:4000/.

# Content

## Pages

Pages (uncategorized, undated content pages) are all organized under the
`/_pages/` folder.

## Collections

Collections (see: [Jekyll Collections](https://jekyllrb.com/docs/collections/))
are all rooted under the `/collections/` folder.

### Posts

Posts (blog entries) should be written under `/collections/_posts/` folder with
the usual Jekyll post file naming scheme (`yyyy-mm-dd-title-with-dashes.md`).

### Categorized Posts

To add categories to a post, place the entry file with the path
`/collections/<category1>/<category2>/_posts/yyyy-mm-dd-title.md`.
