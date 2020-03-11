# normalize-filenames

> A quick-and-dirty Ruby script to perform Unicode Normalization on filesystem paths

## Install

Download, mark as executable, and run from the command line

```
curl -fsSLO https://github.com/jarrodldavis/normalize-filenames/raw/master/normalize-filenames
chmod +x ./normalize-filenames
./normalize-filenames
```

## Usage

```
Usage:
  normalize-filenames unicode PATH -g, --glyph-preservation=PRESERVATION_TYPE -o, --operation=OPERATION

Options:
  -g, --glyph-preservation=PRESERVATION_TYPE  # Whether to preserve glyphs or replace applicable glyphs with compatibility characters
                                              # Default: canonical
                                              # Possible values: canonical, compatibility
  -o, --operation=OPERATION                   # Whether to compose Unicode grapheme clusters into single code points, or decompose them into multi-code-point sequneces
                                              # Default: compose
                                              # Possible values: compose, decompose
  -v, [--verbose], [--no-verbose]             # Print verbose output of every file and folder visited

Perform Unicode normalization on filenames in PATH
```

## Examples

```sh
# normalize all filesystem paths in the current directory to NFC (Composed, Canonical) Form
./normalize-filenames unicode .
```

```sh
# normalize all filesystem paths in the current directory to NFD (Decomposed, Canonical) Form
./normalize-filenames unicode . -o decompose
```

```sh
# normalize all filesystem paths in the current directory to NFKC (Composed, Compatibiltiy) Form
./normalize-filenames unicode . -g compatibility
```

```sh
# normalize all filesystem paths in the current directory to NFKD (Decomposed, Compatibiltiy) Form
./normalize-filenames unicode . -o decompose -g compatibility
```

```sh
# normalize all filesystem paths in the `photos` folder of the current directory to NFC (Composed, Canonical) Form
./normalize-filenames unicode ./photos
```
