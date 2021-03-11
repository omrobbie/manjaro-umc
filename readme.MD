# Universal Modeline Calculator (UMC)
> Setting widescreen display resolution for Manjaro.

By default, my widescreen display resolution is only reach for maximum 1920x1080 resolution which is makes the screen a little bit stretch. I need 2560x1080 as ideal resolution for my display.

![Widescreen display](/screenshot/preview1.png)

So, I've been using the Coordinated Video Timing (CVT) to calculate VESA CVT mode lines with this sample code below:

```bash
cvt 2560 1080 60
```
But it's not working. And I found UMC. You can [download UMC here](https://sourceforge.net/projects/umc/files/umc/umc-0.2/).

After download the UMC, just extract and install it with C compiler or `gcc` and `make`. Manjaro doesn't have it by default, so we have to install it first with `pacman` and run this code after:

```bash
cd umc-0.2
./configure
make install
```

Next, run the UMC with the desire resolution:

```bash
cd umc-0.2/src
./umc 2560 1080 60 --rbt
```

Copy the output result and add new resolution mode using `xrandr` like this example:

```bash
xrandr --newmode "2560x1080x59.98"  181.250000  2560 2608 2640 2720  1080 1083 1087 1111  +HSync -VSync
xrandr --addmode HDMI3 "2560x1080x59.98"
xrandr --output HDMI3 --mode "2560x1080x59.98" --rotate normal
```

If you see there is HDMI3, it's because my display is on that port. You can use `xrandr` command to find your display port.

This is the result. Now we can use our new display resolution.

![Widescreen display](/screenshot/preview2.png)

### Note
I put the UMC installer here if it's not available anymore.
