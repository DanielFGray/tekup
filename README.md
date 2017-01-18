# tekup
Command line script to upload files to https://teknik.io

## Dependencies

[jq](https://github.com/stedolan/jq) - for parsing JSON response

## Usage

```
Usage: tekup [OPTIONS] FILES..
  -h           print this help
  -v           print verbose output. can be stacked. there are two levels of
               verbosity (because this thing is over-engineered), the first
               will print the JSON response from teknik, the second will also
               pass the -v option to curl
  -d           request a deletion key for images
  -e <STRING>  expiration time. only has an effect on text pastes.
               must be in the form of 'N UNITS' where N is a number
               and UNIT is one of the following:
               minute hour day month year
```

## Example:

`` bash
tekup -e '5 minutes' -d some.txt some.png
``

This will upload two files, `some.txt` will self-destruct after 5 minutes, and will also print a url that will delete `some.png`.

## See also

* [yaxg](https://github.com/DanielFGray/yaxg) - for recording screenshots
