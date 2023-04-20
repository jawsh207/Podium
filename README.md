# Podium <!-- omit in toc -->

A straight copy of GoToSocial intended to be better by enabling full support for Soapbox and other projects that the main developers refuse to work with.

Podium is an [ActivityPub](https://activitypub.rocks/) social network server, written in Golang.

With Podium, you can keep in touch with your friends, post, read, and share images and articles. All without being tracked or advertised to!

<p align="middle">
  <img src="./docs/assets/sloth.png" width="300"/>
</p>

**Podium is still [ALPHA SOFTWARE](https://en.wikipedia.org/wiki/Software_release_life_cycle#Alpha)**. It is already deployable and useable, and it federates cleanly with many other Fediverse servers (not yet all). However, many things are not yet implemented, and there are plenty of bugs! We foresee entering beta somewhere in 2023.

Podium is a fork of GoToSocial that aims to add full support for Soapbox FE.

Documentation is at [docs.gotosocial.org](https://docs.gotosocial.org). You can skip straight to the API documentation [here](https://docs.gotosocial.org/en/latest/api/swagger/). To build from source, check the [CONTRIBUTING.md](./CONTRIBUTING.md) file.


## What is Podium?

Podium provides a lightweight, customizable, and safety-focused entryway into the [Fediverse](https://en.wikipedia.org/wiki/Fediverse), and is comparable to (but distinct from) existing projects such as [Mastodon](https://joinmastodon.org/), [Pleroma](https://pleroma.social/), [Friendica](https://friendi.ca), and [PixelFed](https://pixelfed.org/).

If you've ever used something like Twitter or Tumblr (or even Myspace!) Podium will probably feel familiar to you, especially when paired with Soapbox: You can follow people and have followers, you make posts which people can favourite and reply to and share, and you scroll through posts from people you follow using a timeline. You can write long posts or short posts, or just post images, it's up to you. You can also, of course, block people or otherwise limit interactions that you don't want by posting just to your friends.

**Podium does NOT use recommendation algorithms or collect data about you to suggest content or 'improve your experience'**. The timeline is chronological: whatever you see at the top of your timeline is there because it's *just been posted*, not because it's been selected as interesting (or controversial) based on your personal profile.

Podium is not designed for 'must-follow' influencers with tens of thousands of followers, and it's not designed to be addictive. Your timeline and your experience are shaped by who you follow and how you interact with people, not by metrics of engagement!

Podium doesn't claim to be *better* than any other application, but it offers something that might be better *for you* in particular.

### Federation

Because Podium uses [ActivityPub](https://activitypub.rocks/), you can hang out not just with people on your home server, but with people all over the [Fediverse](https://en.wikipedia.org/wiki/Fediverse), seamlessly.

![the activitypub logo](docs/assets/ap_logo.svg)

Federation means that your home server is part of a network of servers all over the world that all communicate using the same protocol. Your data is no longer centralized on one company's servers, but resides on your own server and is shared — as you see fit — across a resilient web of servers run by other people.

This federated approach also means that you aren't beholden to arbitrary rules from some gigantic corporation potentially thousands of miles away. Your server has its own rules and culture; your fellow server residents are your neighbors; you will likely get to know your server admins and moderators, or be an admin yourself.

Podium advocates for many small, weird, specialist servers where people can feel at home, rather than a few big and generic ones where one person's voice can get lost in the crowd.

## Features

### Mastodon API compatibility

The Mastodon API has become the de facto standard for client communication with federated servers, so Podium has implemented and extended the API with custom functionality.

In short, this means full support for modern, beautiful apps like [Tusky](https://tusky.app/) and [Pinafore](https://pinafore.social/).

Tusky                                                        |  Pinafore
:-----------------------------------------------------------:|:------------------------------------------------------------------:
![An image of Podium in Tusky](./docs/assets/tusky.png)  | ![An image of Podium in Pinafore](./docs/assets/pinafore.png)

If you're used to using Mastodon with Tusky or Pinafore, you'll find using Podium a breeze.

### Granular post settings

It's important that when you post something, you can choose who sees it.

Podium offers public/unlisted/friends-only/mutuals-only/and direct posts (slide in DMs! -- with consent).

It also allows you to customize how people interact with your posts:

- Local-only posts.
- Rebloggable/boostable toggle.
- 'Likeable' toggle.
- 'Replyable' toggle.

### Customizability for admins

Plenty of [config options](./example/config.yaml) for admins to play around with, including:

- Easily adjustable post length.
- Media upload size settings.

### Easy to run

No external dependencies apart from a database (or just use SQLite!). Simply download the binary + assets (or Docker container), and run.

Podium plays nice with lower-powered machines like Raspberry Pi, old laptops and tiny $5/month VPSes.

### Safety + security features

- Built-in, automatic support for secure HTTPS with [Let's Encrypt](https://letsencrypt.org/).
- Strict privacy enforcement for posts and strict blocking logic.
- Import and export allow lists and deny lists. Subscribe to community-created block lists (think Ad blocker, but for federation!).
- HTTP signature authentication: Podium requires [HTTP Signatures](https://tools.ietf.org/id/draft-cavage-http-signatures-01.html) when sending and receiving messages, to ensure that your messages can't be tampered with and your identity can't be forged.

### Various federation modes

Podium doesn't apply a one-size-fits-all approach to federation. Who your server federates with should be up to you.

- 'Normal' federation; discover new servers.
- *Allow list*-only federation; choose which servers you talk to.
- Zero federation; keep your server private.

### OIDC integration

Podium supports [OpenID Connect (OIDC)](https://openid.net/connect/) identity providers, meaning you can integrate it with existing user management services like [Auth0](https://auth0.com/), [Gitlab](https://docs.gitlab.com/ee/integration/openid_connect_provider.html), etc., or run your own and hook GtS up to that (we recommend [Dex](https://dexidp.io/)).

### Backend-first design

Unlike other federated server projects, Podium doesn't include an integrated client front-end (i.e., a web app).

Instead, like Matrix.org's [Synapse](https://github.com/matrix-org/synapse) project, it provides a relatively generic backend server implementation, some beautiful static pages for profiles and posts, and a [well-documented API](https://docs.gotosocial.org/en/latest/api/swagger/).

On top of this API, web developers are encouraged to build any front-end implementation or mobile application that they wish, whether Tumblr-like, Facebook-like, Twitter-like, or something else entirely.

## Wishlist

These cool things will be implemented if time allows (because we really want them):

- **Groups** and group posting!
- Reputation-based 'slow' federation.
- Community decision-making for federation and moderation actions.
- User-selectable custom templates for rendering public posts:
  - Twitter-style
  - Blogpost
  - Gallery
  - Etc.

## Getting Started

All docs for installation and configuration are hosted at [docs.gotosocial.org](https://docs.gotosocial.org).

## Known Issues

Since Podium is still in alpha, there are plenty of bugs. We use [GitHub issues](https://github.com/superseriousbusiness/gotosocial/issues?q=is%3Aissue+is%3Aopen+label%3Abug) to track these. The [FAQ](docs/faq.md) also describes some of the features that haven't been implemented yet.

### Client App Issues

Podium works great with Tusky and Pinafore, but some other client applications still need work or have issues connecting to Podium. It's our goal to make any app that's compatible with the Mastodon API work seamlessly with Podium, with a strong focus on Soapbox.

### Federation Issues

Since every ActivityPub server implementation has a slightly different interpretation of the protocol, some servers don't quite federate properly with Podium yet. Eventually, we want to make sure that any implementation that can federate nicely with Mastodon should also be able to federate with Podium.

## Contributing

You would like to contribute to Podium? Great! ❤️❤️❤️ Check out the issues page to see if there's anything you intend to jump in on, and read the [CONTRIBUTING.md](./CONTRIBUTING.md) file for guidelines and setting up your dev environment.

## Building

Instructions for building Podium from source are in the [CONTRIBUTING.md](./CONTRIBUTING.md) file.

## Contact

For bugs and feature requests, please check to see if there's [already an issue](https://github.com/jawsh207/Podium/issues), and if not, open one.

## Credits

### Libraries

The following libraries and frameworks are used by Podium, with gratitude 💕

- [abema/go-mp4](https://github.com/abema/go-mp4); mp4 parsing. [MIT License](https://spdx.org/licenses/MIT.html).
- [buckket/go-blurhash](https://github.com/buckket/go-blurhash); used for generating image blurhashes. [GPL-3.0 License](https://spdx.org/licenses/GPL-3.0-only.html).
- [coreos/go-oidc](https://github.com/coreos/go-oidc); OIDC client library. [Apache-2.0 License](https://spdx.org/licenses/Apache-2.0.html).
- [disintegration/imaging](https://github.com/disintegration/imaging); image resizing. [MIT License](https://spdx.org/licenses/MIT.html).
- [gin-gonic/gin](https://github.com/gin-gonic/gin); speedy router engine. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gin-contrib/cors](https://github.com/gin-contrib/cors); Gin CORS middleware. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gin-contrib/gzip](https://github.com/gin-contrib/gzip); Gin gzip middleware. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gin-contrib/sessions](https://github.com/gin-contrib/sessions); Gin sessions middleware. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gin-contrib/static](https://github.com/gin-contrib/static); Gin static page middleware. [MIT License](https://spdx.org/licenses/MIT.html).
- [go-fed/httpsig](https://github.com/go-fed/httpsig); secure HTTP signature library. [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html).
- [google/uuid](https://github.com/google/uuid); UUID generation. [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html).
- [google/wuffs](https://github.com/google/wuffs); png-stripping code. [Apache-2.0 License](https://spdx.org/licenses/Apache-2.0.html).
- [go-playground/validator](https://github.com/go-playground/validator); struct validation. [MIT License](https://spdx.org/licenses/MIT.html).
- [gorilla/feeds](https://github.com/gorilla/feeds); RSS + Atom feed generation. [BSD-2-Clause License](https://spdx.org/licenses/BSD-2-Clause.html).
- [gorilla/websocket](https://github.com/gorilla/websocket); Websocket connectivity. [BSD-2-Clause License](https://spdx.org/licenses/BSD-2-Clause.html).
- gruf's libraries:
  - [gruf/go-debug](https://codeberg.org/gruf/go-debug); debug build tag. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-bytesize](https://codeberg.org/gruf/go-bytesize); byte size parsing / formatting. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-cache](https://codeberg.org/gruf/go-cache); object & result caching. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-errors](https://codeberg.org/gruf/go-errors); performant multi-error checking [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-fastcopy](https://codeberg.org/gruf/go-fastcopy); performant pooled I/O copying [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-kv](https://codeberg.org/gruf/go-kv); log field formatting. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-mutexes](https://codeberg.org/gruf/go-mutexes); safemutex & mutex map. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-runners](https://codeberg.org/gruf/go-runners); workerpools and synchronization. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-sched](https://codeberg.org/gruf/go-sched); task scheduler. [MIT License](https://spdx.org/licenses/MIT.html).
  - [gruf/go-store](https://codeberg.org/gruf/go-store); file storage backend (local & s3). [MIT License](https://spdx.org/licenses/MIT.html).
- [h2non/filetype](https://github.com/h2non/filetype); filetype checking. [MIT License](https://spdx.org/licenses/MIT.html).
- [jackc/pgx](https://github.com/jackc/pgx); Postgres driver. [MIT License](https://spdx.org/licenses/MIT.html).
- [mcuadros/go-syslog](https://github.com/mcuadros/go-syslog); Syslog server library. [MIT License](https://spdx.org/licenses/MIT.html).
- [microcosm-cc/bluemonday](https://github.com/microcosm-cc/bluemonday); HTML user-input sanitization. [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html).
- [miekg/dns](https://github.com/miekg/dns); DNS utilities. [Go License](https://go.dev/LICENSE).
- [mitchellh/mapstructure](https://github.com/mitchellh/mapstructure); Go interface => struct parsing. [MIT License](https://spdx.org/licenses/MIT.html).
- [modernc.org/sqlite](https://gitlab.com/cznic/sqlite); cgo-free port of SQLite. [Other License](https://gitlab.com/cznic/sqlite/-/blob/master/LICENSE).
  - [modernc.org/ccgo](https://gitlab.com/cznic/ccgo); c99 AST -> Go translater. [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html).
  - [modernc.org/libc](https://gitlab.com/cznic/libc); C-runtime services. [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html).
- [mvdan/xurls](https://github.com/mvdan/xurls); URL parsing regular expressions. [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html).
- [oklog/ulid](https://github.com/oklog/ulid); sequential, database-friendly ID generation. [Apache-2.0 License](https://spdx.org/licenses/Apache-2.0.html).
- [ReneKroon/ttlcache](https://github.com/ReneKroon/ttlcache); in-memory caching. [MIT License](https://spdx.org/licenses/MIT.html).
- [robfig/cron](https://github.com/robfig/cron); cron job scheduling. [MIT License](https://spdx.org/licenses/MIT.html).
- [russross/blackfriday](https://github.com/russross/blackfriday); markdown parsing for statuses. [Simplified BSD License](https://spdx.org/licenses/BSD-2-Clause.html).
- [spf13/cobra](https://github.com/spf13/cobra); command-line tooling. [Apache-2.0 License](https://spdx.org/licenses/Apache-2.0.html).
- [spf13/pflag](https://github.com/spf13/pflag); command-line flag utilities. [Apache-2.0 License](https://spdx.org/licenses/Apache-2.0.html).
- [spf13/viper](https://github.com/spf13/viper); configuration management. [Apache-2.0 License](https://spdx.org/licenses/Apache-2.0.html).
- [stretchr/testify](https://github.com/stretchr/testify); test framework. [MIT License](https://spdx.org/licenses/MIT.html).
- [superseriousbusiness/exif-terminator](https://github.com/superseriousbusiness/exif-terminator); EXIF data removal. [GNU AGPL v3 LICENSE](https://spdx.org/licenses/AGPL-3.0-or-later.html).
- [superseriousbusiness/activity](https://github.com/superseriousbusiness/activity) forked from [go-fed/activity](https://github.com/go-fed/activity); Golang ActivityPub/ActivityStreams library. [BSD-3-Clause License](https://spdx.org/licenses/BSD-3-Clause.html).
- [superseriousbusiness/oauth2](https://github.com/superseriousbusiness/oauth2) forked from [go-oauth2/oauth2](https://github.com/go-oauth2/oauth2); OAuth server framework and token handling. [MIT License](https://spdx.org/licenses/MIT.html).
- [go-swagger/go-swagger](https://github.com/go-swagger/go-swagger); Swagger OpenAPI spec generation. [Apache-2.0 License](https://spdx.org/licenses/Apache-2.0.html).
- [tdewolff/minify](https://github.com/tdewolff/minify); HTML minification for Markdown-submitted posts. [MIT License](https://spdx.org/licenses/MIT.html).
- [uptrace/bun](https://github.com/uptrace/bun); database ORM. [BSD-2-Clause License](https://spdx.org/licenses/BSD-2-Clause.html).
- [wagslane/go-password-validator](https://github.com/wagslane/go-password-validator); password strength validation. [MIT License](https://spdx.org/licenses/MIT.html).
- [ulule/limiter](https://github.com/ulule/limiter); http rate limit middleware. [MIT License](https://spdx.org/licenses/MIT.html).

### Image Attribution and Licensing

Sloth logo by [Anna Abramek](https://abramek.art/).

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />The GoToSocial sloth mascot is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.

The Creative Commons Attribution-ShareAlike 4.0 International License license applies specifically to the following files and subdirectories of this repository:

- [sloth logo png](./web/assets/logo.png)
- [sloth logo svg](./web/assets/logo.svg)
- [all default avatars](./web/assets/default_avatars)

Under the terms of the license, you are free to:

- Share — copy and redistribute the abovementioned material in any medium or format.
- Adapt — remix, transform, and build upon the abovementioned material for any purpose, even commercially.

### GoToSocial Team

In alphabetical order (... and order of smell):

- f0x \[[donate with liberapay](https://liberapay.com/f0x)\]
- kim \[check out my code @ [codeberg](https://codeberg.org/gruf), or find me @ [@kim](https://k.iim.gay/@kim)\]
- tobi \[[donate with liberapay](https://liberapay.com/GoToSocial/)\]
- maloki \[[@maloki@goblin.technology](https://goblin.technology/@maloki)\]
