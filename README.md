# docker-lex-install
### A CommandBox Module for preloading Lucee extensions (.lex) into your CommandBox Docker deployments.

_This is an early stage project that was initially developed for internal use. Feel free to use the issue tracker to report bugs or suggest improvements._

## What it does
This module automatically loads all provided Lucee extension (.lex) files into the CommandBox server's `/lucee-server/deploy` folder when the server starts. It's intended to be used by [CommandBox deployments](https://hub.docker.com/r/ortussolutions/commandbox/) of Lucee on Docker, in order to make Lucee extensions available while warming up a server, so that they're ready to use when the container is deployed.

There are other approaches to this issue, including the use of the [`LUCEE_EXTENSIONS` environment variable](https://labs.daemon.com.au/t/installing-the-memcached-extension-for-lucee-5-x/319), which you may find preferable, depending on your use case.

Using this module's approach to installing extensions can be particularly helpful when:
1. You want to install a specific version of an extension
2. You don't want to be reliant on HTTP calls to download the extensions from Lucee.org during your build.
3. You want to know exactly what extensions you're installing (instead of bothering with the extension GUIDs)
4. You're using a version of Lucee that doesn't support ENV extension installations.

## Using this module
This module it makes several assumptions about file/folder structure.


### It needs to be a dependency in your `box.json`

TODO

### Extensions need to be in `/config/extensions`

Within the container, on server start (`onServerStart()`), it looks for `.lex` files in: `/config/extensions`. You'll need to load the extensions that you want to use into this folder; your Dockerfile might include something along these lines:

```
# Copy in our config file(s)
# Our local /config folder should include /extensions
COPY ./config/ /config/
```

### `box install` needs to be run

TODO

### The server needs to be warmed up

TODO

## Questions
For questions that aren't about bugs, feel free to hit me up on the [CFML Slack Channel](http://cfml-slack.herokuapp.com); I'm @mjclemente. You'll likely get a much faster response than creating an issue here.

## Contributing
:+1::tada: First off, thanks for taking the time to contribute! :tada::+1:

Before putting the work into creating a PR, I'd appreciate it if you opened an issue. That way we can discuss the best way to implement changes/features, before work is done.

Changes should be submitted as Pull Requests on the `develop` branch.