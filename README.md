# tekup
Command line script to upload files to https://teknik.io

## Usage

```
Usage: tekup [OPTIONS] [FILES..]
  -h          print this help
  -p [NUMBER] use [NUMBER] of concurrent processes to upload files with.
              defaults to 1
  -v          print verbose output. there are two levels of verbosity
              (because this thing is over-engineered), the first will print
              the JSON response from teknik, the second will also pass the
              -v option to curl
```
