# Fixing few GIMP scripts

Running a couple of GIMP scripts gave errors.

See

- https://www.gimp.org/docs/script-fu-update.html


The issues described in that link seem to be already fixed: there are
other issues not stricly related to the change of the language, but
likely to changes in GIMP (2.10.8).

E.g., having `LAYER-MODE-NORMAL` instead of `NORMAL` or `BLEND-LINEAR`
instead of just `LINEAR` it's a good thing, but it breaks code using
the “unprefixed” symbols.


**Note**: those scripts are installed, in my current (as of August, 2019)
Ubuntu 19.04 distro, in `/usr/share/gimp/2.0/scripts/` and GIMP's
version is 2.10.8 as already written.



## planet-render1-2.scm

- `NORMAL` becomes `LAYER-MODE-NORMAL-LEGACY`.

The use of the `-LEGACY` version seems logical. I haven't tried
otherwise.


## xtns-demartin-liquid-water.scm

- `NORMAL` becomes `LAYER-MODE-NORMAL-LEGACY`
- `displace-type` for `plug-in-displace` set to 1 (`WRAP`): 0 isn't in
  the range of accepted values.


## xtns-lankinen-fiery-steel.scm

- `NORMAL`, `OVERLAY` and `ADDITION` become `LAYER-MODE-*-LEGACY`
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


