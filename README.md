# Ayumi's Keyboard Layout

Keyboard: [Infinity 60%](https://www.massdrop.com/buy/infinity-keyboard-kit/?mode=guest_open)

## Instructions

1. Clone [kiibohd controller](https://github.com/kiibohd/controller)
2. (If starting from existing repo) `cd kll` and `git pull` to make sure [kll](https://github.com/kiibohd/kll) is latest.
3. Copy layout files `yumi.kll` and `yumi-overlay.kll` into `kll/layouts`.
4. In kiibohd root directory, `mkdir build-yumi && cd build-yumi`.
5. Configure cmake:
```sh
cmake -DCHIP=mk20dx128vlf5 -DScanModule=MD1 -DMacroModule=PartialMap \                                          11:42:05
  -DOutputModule=pjrcUSB -DDebugModule=full -DBaseMap=defaultMap \
  -DDefaultMap="yumi stdFuncMap" -DPartialMaps="yumi-overlay" ../
```
6. Build with `make`
7. Push keyboard flashy button then run `sudo dfu-util -D kiibohd.dfu.bin`.

### Windows

Configure cmake with an additional KLL layer, yumi-windows:

```sh
cmake -DCHIP=mk20dx128vlf5 -DScanModule=MD1 -DMacroModule=PartialMap \                                          11:42:05
  -DOutputModule=pjrcUSB -DDebugModule=full -DBaseMap=defaultMap \
  -DDefaultMap="yumi-windows yumi stdFuncMap" -DPartialMaps="yumi-overlay" ../
```

### Rebuilding

kiibohd gets updated a lot, so it's a good idea to upgrade the firmware periodically.

Create a new directory and repeat instructions 5-7.
