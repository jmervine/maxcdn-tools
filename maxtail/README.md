maxtail - alpha
===============

"tail" (sort of) MaxCDN endpoints, return raw json output.

```
Usage: maxtail [arguments...] PATH

Example:

    $ maxtail -a ALIAS -t TOKEN -s SECRET -i 5

Options:

   --config, -c '~/.maxcdn.yml'	yaml file containing all required args
   --alias, -a 			[required] consumer alias
   --token, -t 			[required] consumer token
   --secret, -s 		[required] consumer secret
   --format, -f 'raw'		nginx, raw, json, jsonpp
   --interval, -i '5'		poll interval in seconds (min: 5)
   --no-follow, -n		print interval and exit
   --quiet, -q			hide 'empty' messages
   --verbose			display verbose http transport information
   --zones 			filter: by zone(s)
   --uri 			filter: uri
   --status 			filter: status
   --ssl 			filter: ssl
   --ua 			filter: user agent
   --referer 			filter: referer
   --pop 			filter: pop
   --qs 			filter: query string
   --version, -v		print the version
   --help, -h			show help


Formatting Notes:

- "raw"    is basic print of struct.
- "jsonpp" is multiline human readable json output.
- "json"   is single-line parseable json output.
- "nginx"  emulates nginx's default log format...

    Nginx Format
    ------------
    'ClientIp CacheStatus ZoneID [Time] "Uri" '
    'Status Bytes Referer UserAgent OriginTime'

Filter Notes:

- "zones":
    The specific zones whose requests you want to pull.  Separate
    multiple zone ids by comma.
- "uri":
    Use this filter to view requests made for a specific resource
    (or group of resources). You can do a literal match or regular
    expression in this field (i.e. '/images/header.png' or
    'regex:/images/').
- "status":
    The specific HTTP status code responses you want to pull.
    Separate multiple HTTP status codes by comma (i.e. 200,201,304).
- "ssl":
    Use this filter to distinguish between SSL and non-SSL traffic
    (choose nossl, ssl or both).
- "ua":
    Filter logs by specific user agents. You can do a literal match
    or regular expression in this field (i.e. 'Python MaxCDN API
    Client' or 'regex:Chrome').
- "referer":
    Filter logs by a specific referer. You can do a literal match or
    regular expression in this field (i.e. 'www.maxcdn.com' or
    'regex:maxcdn.com').
- "pop":
    Filter logs by specific POPs (Points Of Presence), use comma
    separation for multiple POPs.
- "qs":
    Filter logs by a specific query string. You can do a literal
    match or regular expression in this field (i.e. 'width=600' or
    'regex:width').

See https://docs.maxcdn.com/#get-raw-logs for full details.

Alpha Notes:

- There is a built in 15 second delay on events.
- Does not currently show all events while in follow mode. However,
  the more you filters applied, the closer it will be to displaying
  all events.

Credential Notes:

'alias', 'token' and/or 'secret' can be set via exporting them to
your environment and ALIAS, TOKEN and/or SECRET.

Additionally, they can be set in a YAML configuration via the
config option. 'pretty' and 'host' can also be set via
configuration, but not environment.

Precedence is argument > environment > configuration.

WARNING:
    Default configuration path works for *nix systems only and
    replies on the 'HOME' environment variable. For Windows, please
    supply a full path.

Sample configuration:

    ---
    alias: YOUR_ALIAS
    token: YOUR_TOKEN
    secret: YOUR_SECRET
    pretty: true

```

Download:
---------

- [linux/386](http://get.maxcdn.com/maxtail/linux/386/maxtail) ([md5](http://get.maxcdn.com/maxtail/linux/386/maxtail.md5))
- [linux/amd64](http://get.maxcdn.com/maxtail/linux/amd64/maxtail) ([md5](http://get.maxcdn.com/maxtail/linux/amd64/maxtail.md5))
- [linux/arm](http://get.maxcdn.com/maxtail/linux/arm/maxtail) ([md5](http://get.maxcdn.com/maxtail/linux/arm/maxtail.md5))
- [darwin/386](http://get.maxcdn.com/maxtail/darwin/386/maxtail) ([md5](http://get.maxcdn.com/maxtail/darwin/386/maxtail.md5))
- [darwin/amd64](http://get.maxcdn.com/maxtail/darwin/amd64/maxtail) ([md5](http://get.maxcdn.com/maxtail/darwin/amd64/maxtail.md5))
- [freebsd/386](http://get.maxcdn.com/maxtail/freebsd/386/maxtail) ([md5](http://get.maxcdn.com/maxtail/freebsd/386/maxtail.md5))
- [freebsd/amd64](http://get.maxcdn.com/maxtail/freebsd/amd64/maxtail) ([md5](http://get.maxcdn.com/maxtail/freebsd/amd64/maxtail.md5))
- [freebsd/arm](http://get.maxcdn.com/maxtail/freebsd/arm/maxtail) ([md5](http://get.maxcdn.com/maxtail/freebsd/arm/maxtail.md5))
- [windows/386](http://get.maxcdn.com/maxtail/windows/386/maxtail.exe) ([md5](http://get.maxcdn.com/maxtail/windows/386/maxtail.exe.md5))
- [windows/amd64](http://get.maxcdn.com/maxtail/windows/amd64/maxtail.exe) ([md5](http://get.maxcdn.com/maxtail/windows/amd64/maxtail.exe.md5))


Build and Install:
------------------

This can also be installed for system wide use if your `GOBIN` is set via the following:

```bash
# via 'go get' && 'go install'
##

$ go get github.com/MaxCDN/maxcli/maxtail
$ go install github.com/MaxCDN/maxcli/maxtail
$ maxtail -h
Usage: maxtail [arguments...] PATH
# ...

# manually
##

git clone https://github.com/MaxCDN/maxcli
cd maxcli
make build/maxtail install/maxtail
```
