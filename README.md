# nice-view-module

![Preview](https://github.com/TurnipBlue/nice-view-module/blob/main/.github/assets/preview.jpg?raw=true)

## Usage

To use this module, first add it to your `config/west.yml` by adding a new entry to remotes and projects:

```yml
manifest:
  remotes:
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    - name: turnipblue                         # new entry
      url-base: https://github.com/TurnipBlue  # new entry
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: main
      import: app/west.yml
    - name: nice-view-module  # new entry
      remote: turnipblue      # new entry
      revision: main          # new entry
  self:
    path: config
```

Now, simply swap out the default *nice_view* shield on the board for *nice_view_module* in your `build.yaml` file:

```yml
include:
  - board: nice_nano_v2
    shield: corne_left nice_view_adapter nice_view_module   # updated entry
  - board: nice_nano_v2
    shield: corne_right nice_view_adapter nice_view_module  # updated entry
```

Finally, you may need to enable the custom status screen in your `config/~~corne~~.conf` file:

```conf
CONFIG_ZMK_DISPLAY=y
CONFIG_ZMK_DISPLAY_STATUS_SCREEN_CUSTOM=y
```

## Configuration

Modify the behavior of this shield by adjusting these options in your personal configuration files. For a more detailed explanation, refer to [Configuration in the ZMK documentation](https://zmk.dev/docs/config).

| Option                             | Type | Description                                      | Default |
| ---------------------------------- | ---- | ------------------------------------------------ | ------- |
| `CONFIG_NICE_VIEW_WIDGET_INVERTED` | bool | To enable color inversion, set the option to `y` | n       |

## License
This module uses the [source code](https://github.com/zmkfirmware/zmk/tree/main/app/boards/shields/nice_view) of the nice!view shield from [ZMK Firmware](https://github.com/zmkfirmware/zmk/tree/main), distributed under the MIT license.
