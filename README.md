# Luminebear's Imagination Hub

Operations repository for a personal Jekyll blog: https://luminebear.github.io

## Current setup

- Minimal Mistakes: `4.21.0`, pinned in Gemfile.
- Jekyll: `4.3.4`, as recorded in the current Gemfile.lock.
- Ruby: `4.0.6`; Bundler: `2.5.23`.
- Local build and preview tested on Fedora 44 Server.
- GitHub Actions uses `ubuntu-24.04` with the Ruby and Bundler versions above.
- Theme configuration: `theme: minimal-mistakes-jekyll` in `_config.yml`.
- Default layouts, includes, Sass, and JavaScript are supplied by the theme gem.
- Site content, settings, and required custom overrides are maintained in this repository.
- Gemfile and Gemfile.lock define the dependencies. The theme has not yet been upgraded.

## Build and preview

Run these commands from the repository root in a Linux shell.

```bash
bundle _2.5.23_ check
```

On a new environment with missing dependencies, review the setup and run
`bundle _2.5.23_ install` to install the locked dependencies.
Do not run `bundle update` for routine writing or builds.

Standard build and preview commands:

```bash
JEKYLL_ENV=production bundle _2.5.23_ exec jekyll build --trace
bundle _2.5.23_ exec jekyll serve --host 127.0.0.1 --port 4000
```

In the tested Fedora 44 Server environment, a non-interactive SSH session could
not locate the `jekyll` executable even though the required gems were installed.
Before reinstalling gems or changing settings, use the installed executable
directly. This invocation was verified for both build and preview:

```bash
jekyll_path=$(bundle _2.5.23_ show jekyll)
JEKYLL_ENV=production bundle _2.5.23_ exec ruby "$jekyll_path/exe/jekyll" build --trace
bundle _2.5.23_ exec ruby "$jekyll_path/exe/jekyll" serve --host 127.0.0.1 --port 4000
```

Open http://127.0.0.1:4000 on the machine running the preview.
For a remote server, use VSCode port forwarding or an SSH tunnel configured
for your own host. Keep the preview bound to the loopback interface.

If port 4000 is occupied, select another port and adjust forwarding accordingly.
Stop the server and any tunnel with Ctrl+C in their respective terminals.
Restart the preview server after changing `_config.yml`.
The old `rake preview` task targeted the theme's test site and is no longer used.
An npm build is not required to regenerate theme JavaScript.

## Review and deployment

1. Create a working branch from the latest master and make small changes.
2. Build locally, check the rendered site, commit, and publish the branch.
3. Open a pull request targeting master and confirm the GitHub Actions build succeeds.
4. Merge after review and approval. A push to master triggers build and deployment.
5. Verify the public site as well as the Actions results.

The workflow is defined in `.github/workflows/jekyll.yml`.
GitHub Pages uses GitHub Actions as its deployment source.
Pull requests run the build but skip deployment.
A push to an ordinary working branch does not trigger this workflow by itself;
open a pull request for validation.
The current workflow also allows pushes to `maintenance/pages-build-validation`
and manual runs. Deployment is restricted to master push events or manual runs
on master.
The `runs-on: ubuntu-24.04` setting selects the GitHub runner; it does not change
the local server's operating system.

## Customizations to preserve

| Location | Purpose |
| --- | --- |
| `_includes/head/custom.html` | Dark-mode toggle, sessionStorage restoration, conditional MathJax loading |
| `_includes/mathjax-support.html` | MathJax configuration and loading; enabled by `mathjax: true` in a post |
| `assets/css/main.scss` | Default dirt skin, #fff background, #1a1a1a text, font loading |
| `assets/css/theme2.scss` | Dark skin and font loading |
| `_sass/custom/_variables.scss` | MaruBuri, NanumSquare, NanumSquareRound, D2 Coding font families; x-large 1366px and max-width 1600px |
| `_sass/custom/_typography.scss` | Responsive font sizes of 14/16/18/18px |
| `_sass/custom/_dark.scss` | Dark-theme icon color adjustments |
| `_data/navigation.yml` | Site navigation |

Posts are stored in `_posts/`; images and attachments are in `assets/images/`
and `files/`. Avoid copying the entire theme back into the repository or editing
installed gem files directly.

## Before upgrading the theme

- Check the working tree and baseline commit; use a separate branch.
- Review Gemfile version changes together with Gemfile.lock changes.
- Verify dark mode and stored preferences, equations, fonts, responsive sizes, and widths.
- Check search, navigation, the table of contents, image popups, posts, categories, and tags.
- Check build output, sitemap, feed, GitHub Actions results, and the deployed site.
- Resolve conflicts with existing customizations explicitly rather than removing them silently.
- Distinguish existing warnings, such as Sass deprecations, from new errors.

## Theme attribution and notices

This blog uses Michael Rose's [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes).
The original Credits and License notices are preserved below.
These notices concern the theme and its included components; they do not separately
grant permission to reuse all personal posts or images.
The repository's [LICENSE](LICENSE) file is also retained.

---

## Credits

### Creator

**Michael Rose**

- <https://mademistakes.com>
- <https://twitter.com/mmistakes>
- <https://github.com/mmistakes>

### Icons + Demo Images:

- [The Noun Project](https://thenounproject.com) -- Garrett Knoll, Arthur Shlain, and [tracy tam](https://thenounproject.com/tracytam)
- [Font Awesome](http://fontawesome.io/)
- [Unsplash](https://unsplash.com/)

### Other:

- [Jekyll](http://jekyllrb.com/)
- [jQuery](http://jquery.com/)
- [Susy](http://susy.oddbird.net/)
- [Breakpoint](http://breakpoint-sass.com/)
- [Magnific Popup](http://dimsemenov.com/plugins/magnific-popup/)
- [FitVids.JS](http://fitvidsjs.com/)
- [GreedyNav.js](https://github.com/lukejacksonn/GreedyNav)
- [Smooth Scroll](https://github.com/cferdinandi/smooth-scroll)
- [Gumshoe](https://github.com/cferdinandi/gumshoe)
- [jQuery throttle / debounce](http://benalman.com/projects/jquery-throttle-debounce-plugin/)
- [Lunr](http://lunrjs.com)

---

## License

The MIT License (MIT)

Copyright (c) 2013-2020 Michael Rose and contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Minimal Mistakes incorporates icons from [The Noun Project](https://thenounproject.com/) 
creators Garrett Knoll, Arthur Shlain, and tracy tam.
Icons are distributed under Creative Commons Attribution 3.0 United States (CC BY 3.0 US).

Minimal Mistakes incorporates [Font Awesome](http://fontawesome.io/),
Copyright (c) 2017 Dave Gandy.
Font Awesome is distributed under the terms of the [SIL OFL 1.1](http://scripts.sil.org/OFL) 
and [MIT License](http://opensource.org/licenses/MIT).

Minimal Mistakes incorporates photographs from [Unsplash](https://unsplash.com).

Minimal Mistakes incorporates [Susy](http://susy.oddbird.net/),
Copyright (c) 2017, Miriam Eric Suzanne.
Susy is distributed under the terms of the [BSD 3-clause "New" or "Revised" License](https://opensource.org/licenses/BSD-3-Clause).

Minimal Mistakes incorporates [Breakpoint](http://breakpoint-sass.com/).
Breakpoint is distributed under the terms of the [MIT/GPL Licenses](http://opensource.org/licenses/MIT).

Minimal Mistakes incorporates [FitVids.js](https://github.com/davatron5000/FitVids.js/),
Copyright (c) 2013 Dave Rubert and Chris Coyier.
FitVids is distributed under the terms of the [WTFPL License](http://www.wtfpl.net/).

Minimal Mistakes incorporates [Magnific Popup](http://dimsemenov.com/plugins/magnific-popup/),
Copyright (c) 2014-2016 Dmitry Semenov, http://dimsemenov.com.
Magnific Popup is distributed under the terms of the MIT License.

Minimal Mistakes incorporates [Smooth Scroll](http://github.com/cferdinandi/smooth-scroll),
Copyright (c) 2019 Chris Ferdinandi.
Smooth Scroll is distributed under the terms of the [MIT License](http://opensource.org/licenses/MIT).

Minimal Mistakes incorporates [Gumshoejs](http://github.com/cferdinandi/gumshoe),
Copyright (c) 2019 Chris Ferdinandi.
Smooth Scroll is distributed under the terms of the [MIT License](http://opensource.org/licenses/MIT).

Minimal Mistakes incorporates [jQuery throttle / debounce](http://benalman.com/projects/jquery-throttle-debounce-plugin/),
Copyright (c) 2010 "Cowboy" Ben Alman.
jQuery throttle / debounce is distributed under the terms of the [MIT License](http://opensource.org/licenses/MIT).

Minimal Mistakes incorporates [GreedyNav.js](https://github.com/lukejacksonn/GreedyNav),
Copyright (c) 2015 Luke Jackson.
GreedyNav.js is distributed under the terms of the [MIT License](http://opensource.org/licenses/MIT).

Minimal Mistakes incorporates [Jekyll Group-By-Array](https://github.com/mushishi78/jekyll-group-by-array),
Copyright (c) 2015 Max White <mushishi78@gmail.com>.
Jekyll Group-By-Array is distributed under the terms of the [MIT License](http://opensource.org/licenses/MIT).

Minimal Mistakes incorporates [@allejo's Pure Liquid Jekyll Table of Contents](https://allejo.io/blog/a-jekyll-toc-in-liquid-only/),
Copyright (c) 2017 Vladimir Jimenez.
Pure Liquid Jekyll Table of Contents is distributed under the terms of the [MIT License](http://opensource.org/licenses/MIT).

Minimal Mistakes incorporates [Lunr](http://lunrjs.com),
Copyright (c) 2018 Oliver Nightingale.
Lunr is distributed under the terms of the [MIT License](http://opensource.org/licenses/MIT).
