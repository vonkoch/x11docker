Experimental code. Please use [master branch](https://github.com/mviereck/x11docker) instead.



| Option | Description |
| --- | --- |
| --desktop | Indicates a desktop environment in image, and x11docker will try to provide a nested X server setup e.g. with `--xephyr`. Otherwise x11docker assumes a single application and tries to seamlessly integrate it into already running desktop. | 
| --clipboard | - Image clips are possible with `--xpra` and `--hostdisplay`. 
|             | - Some X server options need package `xclip` on host. |


| X server option | Description |
| --- | --- |
| `--auto` (default) | Automatically chooses an X server depending on installed dependencies and on given or missing options `--desktop`, `--gpu` and `--wayland`. |
| `--xpra` | Seamless integration of application windows on host display. Best `--clipboard` support, picture clips are possible.  Seamless scaling (0,5x, 1.5x, 3x ...) with option `--scale`. Supports option `--desktop`, too, but `--xephyr` is more performant in desktop mode. |
| `--xephyr` | Nested X server for `--desktop`  mode. Desktop appears in a window on host display. |
| `--nxagent` | Fast and resizeable alternative to `--xpra` and `--xephyr`, but some compositing applications may fail. |
| `--hostdisplay` | Shares host display `:0` instead of running second X server. ***Attention: Low security, quite bad container isolation!*** Some x11docker security restrictions to avoid keylogging and remote host control may cause some applications to fail. Options `--clipboard` and `--gpu` remove these restrictions. If security is not a concern, get a quite fast setup with `--hostdisplay --gpu`. |
| `--xorg` | Core Xorg server. Switch between displays with keys `[CTRL][ALT][F1]...[F12]`. |
| `--xpra-xwayland` | Like `--xpra`, additionally supporting option `--gpu`. Uses Weston and Xwayland in background. Supports option `--desktop`, too, but `--weston-xwayland` is more performant in desktop mode. |
| `--weston-xwayland` | All-rounder: can run nested on X or Wayland in a window or on its own from console. Supports GPU acceleration, scaling (2x, 3x, 4x ...) and display rotation (0°, 90°, 180°, 270°, flipped, flipped-90°, ...). |
| `--xwayland` | Core Xwayland needs a Wayland environment to run in. Fullscreen display can be moved around with `[META][LMB]`. |
| `--xdummy` `--xvfb` | Invisible X server for custom access. Output of environment variables on stdout. With `--gpu` a setup with Weston, Xwayland and xdotool is used (instead of Xdummy or Xvfb). |
| `--weston` | Weston without X to run pure Wayland applications. Runs in X, in Wayland and from console. Scaling and rotation is possible. |
| `--kwin-xwayland` | Like `--weston-xwayland`, but uses KWin instead of Weston. Runs in X, in Wayland and from console. |
| `--kwin` | kwin_wayland without X to run pure Wayland applications. Runs in X, in Wayland and from console. |
| `--hostwayland` | Shares host wayland socket without X to run pure Wayland applications. Needs a running Wayland compositor. |
