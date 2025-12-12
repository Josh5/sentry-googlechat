# Sentry plugin for Google Chat

A Sentry plugin which posts notifications to [Google Chat](https://gsuite.google.com/products/chat/).


## How will it look like

<img src="https://raw.githubusercontent.com/jweslley/sentry-googlechat/master/notification.png" width="500">


## Requirements

* Sentry 10.0.0 or newer


## Installation

**Now Available on PyPi!** [sentry-googlechat](https://pypi.org/project/sentry-googlechat/)

In your `requirements.txt` file, add the below package name to install the Google Chat Plugin.

```
sentry-googlechat
```

Restart your Sentry instance.


## Configuration

Go to your Sentry web interface and open ``Settings`` page of one of your projects. Locate the Integrations management screen and click 'Configure Plugin' below the 'Google Chat' item.

<img src="https://raw.githubusercontent.com/jweslley/sentry-googlechat/master/configuration.png" width="500">

Create a new Incoming Webhook in Google Chat and paste the URL into the Webhook URL field, then click 'Save Changes'.
There are some other optional configuration options at the moment, but the WebHook URL is the only required field.

When ready, click 'Test Plugin' to generate an exception and send a message to your chosen WebHook URL.

### Tag-specific webhooks

If you want different alerts to go to different spaces, use the new **Tag-specific Webhooks** textarea.
Each line describes one rule in the format `tag_key:tag_value=https://...`. The plugin checks events against the
rules in order and uses the first webhook whose rule matches; if no rule matches it keeps using the default
Webhook URL configured above. Use `*` as a wildcard for the tag key or value and start a line with `#` to add a
comment that will be ignored.

Example:

```
environment:production=https://chat.googleapis.com/v1/spaces/.../prod?key=...
environment:staging=https://chat.googleapis.com/v1/spaces/.../staging?key=...
# fall back to the default webhook
*:*=https://chat.googleapis.com/v1/spaces/.../default?key=...
```


## Bugs and Feedback

If you discover any bugs or have some idea, feel free to create an issue on GitHub:

http://github.com/jweslley/sentry-googlechat/issues


## Support

If you use this or use any of my tools/code, please consider buying me a coffee. Every coffee that you buy, it will be used to develop new free cool stuff ;)

https://www.buymeacoffee.com/jweslley


## License

MIT License. Copyright (c) 2020 [Jonhnny Weslley](<https://www.jonhnnyweslley.net>)
