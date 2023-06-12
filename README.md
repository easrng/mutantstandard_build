# Mutant Standard Build Files

This repository contains all of the files required to build a custom Mutant Standard package using Orxporter.

-----

**These files are for anyone who is techy enough and is interested in seeing what a large Orxporter project looks like, or wants to create their own Mutant Standard packages in a format that's not offered by the website.**

**If you're a regular user, I highly suggest you go to [Mutant Standard's download page](https://mutant.tech/download) and download a package that's best for you.**


-----

## License

Everything in this repository is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-nc-sa/4.0/).


-----

## Requirements

- [Orxporter 0.5.0](https://github.com/mutantstandard/Orxporter/releases)
- [Forc (the latest commit)](https://github.com/mutantstandard/Forc)

There shouldn't be any significant difficulties in using this on various major OSes, and both Orxporter and Forc have been written to be cross-platform. From one time to another these tools have been used on both macOS and Linux.

---


### Images

- Download the latest version of Orxporter.
- Place the Orxporter folder in the root of this directory.
- Start running export commands from the root directory of this repo.

If you want some ideas on how to make your own scripts and commands, in the root of this repo there are `.command` executable scripts, all of which are the ones I use in everyday tests and for the final export of each release.

The [Orxporter repo](https://github.com/mutantstandard/Orxporter/) has full documentation on how to create your own build commands and understand manifest files.


------

## Translating?

Check out the [translation doc](translating.md) for some guidance.

------

## Locations of things

- `/input` is where the input emoji SVGs are.
- `/manifest` is where all the manifest files are, including license metadata.
- `/Orxporter` is where Orxporter should go.
- `/Forc` is where Forc should go.
- `/out` is where the exported emoji go (I recommend putting the output of any task in a sub-folder so you can make multiple types of exports without conflicts).

---

### Fonts

 *(I have decided to stop developing font technology on my end, but it's still easy to compile a font using Orxporter and Forc.)*

- Download the latest version of Orxporter and put it in this folder (as described above), export like this:

```
./Orxporter/orxport.py -m manifest/out.orx -i ../input -q 32x32 -o out/font_sources -F svg,png-32,png-64,png-128 -t 4 -f %f/%u
```

- Download the latest version of Forc.
- Place Forc in the `Forc` directory.
- Then build fonts with Forc like this...


```
./Forc/Forc.py -m manifest/font/manifest.json -a manifest/font/aliases.json -i out/font_sources -o out/fonts -F [formats] --afsc
```

See Forc's help (`-h` flag) to see what formats you can export to. Forc also has a readme and documentation.

(the `--afsc` build flag is super-important if you're building a SVG font with Mutant Standard's images, **do not remove it**.)

