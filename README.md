# Fixing few GIMP scripts

Running a couple of GIMP scripts gave errors.

See

- https://www.gimp.org/docs/script-fu-update.html



## planet-render1-2.scm

It seemed already fixed, except for the use of `NORMAL`, which in GIMP
2.10.8 (from the repository of the GNU/Linux distro Ubuntu 19.04).

`NORMAL` becomes a synonym for `LAYER-MODE-NORMAL-LEGACY`.


## xtns-demartin-liquid-water.scm

Same problem with `NORMAL`; plus, used 0 as `displace-type` argument
for `plug-in-displace`, but accepted values range from 1 to 3 for
the edge behaviour. I've chosen 1 (`WRAP`).


## xtns-lankinen-fiery-steel.scm

- `NORMAL`, `OVERLAY` and `ADDITION` becomes `LAYER-MODE-*-LEGACY`
- `CUSTOM` for `gimp-blend` becomes `BLEND-CUSTOM`
- `LINEAR` for `gimp-blend` becomes `GRADIENT-LINEAR`
- `LINEAR` for `plug-in-bump-map` locally defined as 0


## xtns-demartin-shiny-painting.scm

- `NORMAL` as `LAYER-MODE-*-LEGACY`
- `LINEAR` for `plug-in-bump-map` locally defined as 0


## xtns-gutteridge-dracula.scm

- `NORMAL` as `LAYER-MODE-NORMAL-LEGACY` (using define)

## xtns-mosteller-multi-effect-text.scm

- `plug-in-scatter-hsv` is now `plug-in-hsv-noise`


