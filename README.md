**DEPRECATED**: Use https://github.com/rvaiya/keyd instead

# caps2esc

Remap caps lock to both ctrl (when pressed with another key) and esc (when pressed alone).

## Dependencies

- [Interception Tools][interception-tools]

## Building

```
$ git clone git@gitlab.com:interception/linux/plugins/caps2esc.git
$ cd caps2esc
$ mkdir build
$ cd build
$ cmake ..
$ make
```

## Execution

`caps2esc` is an [_Interception Tools_][interception-tools] plugin. A suggested
`udevmon` job configuration is:

```yaml
- JOB: "intercept -g $DEVNODE | caps2esc | uinput -d $DEVNODE"
  DEVICE:
    EVENTS:
      EV_KEY: [KEY_CAPSLOCK, KEY_ESC]

```

For more information about the [_Interception Tools_][interception-tools], check
the project's website.

## Installation

I'm maintaining an Archlinux package on AUR:

- <https://aur.archlinux.org/packages/interception-caps2esc>

I don't use Ubuntu and recommend Archlinux instead, as it provides the AUR, so I
don't maintain PPAs. For more information on Ubuntu/Debian installation check
this:

- <https://askubuntu.com/questions/979359/how-do-i-install-caps2esc>

## Caveats

As always, there's always a caveat:

- `intercept -g` will "grab" the detected devices for exclusive access.
- If you tweak your key repeat settings, check whether they get reset.
  Please check [this report][key-repeat-fix] about the resolution.

[caps2esc-windows]: https://github.com/oblitum/Interception/blob/master/samples/caps2esc/caps2esc.cpp
[xcape]: https://github.com/alols/xcape
[interception-tools]: https://gitlab.com/interception/linux/tools
[key-repeat-fix]: https://github.com/oblitum/caps2esc/issues/1
