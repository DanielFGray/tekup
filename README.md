# tekup
Command line script to upload files to https://teknik.io

## Dependencies

* [curl](https://github.com/curl/curl) - for network I/O
* [jq](https://github.com/stedolan/jq) - for parsing JSON response

## Usage

```
Usage: tekup [OPTIONS] [FILES...]
  -h           print this help
  -d           request a deletion key for images
  -e <STRING>  expiration time. only has an effect on text pastes.
               must be in the form of 'N UNIT' where N is a number
               and UNIT is one of the following:
               minute hour day month year
  -N           disables expiring pastes (if enabled in config file, for example)
  -v           print verbose output. can be stacked. there are three levels of
               verbosity (because this thing is over-engineered)
               first will show progress from curl
               second will print the json response
               third will show verbose output from curl
```

## Configuration
A configuration file can be defined at `$XDG_CONFIG_DIR/tekup/conf` (defaults to `~/.config/tekup`)  
If a line begins with `#` it is treated as a comment and ignored  
A configuration file has the following options:

```
username       teknik.io username
api_key        teknik.io api key
expire_length  same as -e flag above
do_not_track   asks teknik.io not to log the upload
verbose_level  must be a number
```

If `~/.config/tekup/log` is a writeable file tekup will always ask for a deletion key and log it in that file.

## Example:

``` bash
tekup -e '5 minutes' -d some.txt some.png
```

This will upload two files, `some.txt` will self-destruct after 5 minutes, and will also print a url that will delete `some.png`.

## See also

* [yaxg](https://github.com/DanielFGray/yaxg) - for recording screenshots

## Legal
Copyright (C) 2016 Daniel F Gray <DanielFGray@gmail.com>

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.
