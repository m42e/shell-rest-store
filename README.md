# Shell REST Store
A small script to quickly save files or snippets or whatever by piping them to a command which uses a rest interface to perform the operation. 

It depends on curl, and the REST remote is implemented in PHP and you get it [here](https://github.com/m42e/php-rest-store).

You can use it like this:

```zsh
$ newtmp something
3e3a84fc805d808b0803a4a0012e711bb1612a44
```
You get the sha1 for the tmpid you just created.
``zsh
$ echo This is something | savetmp something mymetainfo/nothing
```
The savetmp will not output anything unless you pipe it into another command
```zsh
$ gettmp savetmp
This is something
```
```gettmp``` just gets you the raw data, ```gettmpjson``` will repack the content into a json object

```zsh
$ gettmp something/meta 
{"written":{"date":"Mon, 13 Jul 2015 19:51:07 +0200","info":{"useragent":"curl\/7.37.1","remote":"18.233.121.21"},"length":18,"accessedvia":"something","meta":{"from":"matthias@matthias-mbp","mymetainfo":"nothing"}}}
```
or better use with [jq](http://stedolan.github.io/jq/) to get a formatted output

You can also append or prepend:
```zsh
$ echo Starting: | prependtmp something
$ echo End | appendtmp something
```

Or upload a file
```zsh
$ newtmp afile
ce25ade3cf7c4c4b5bb61f5447bb8fa9059cc802
$ savetmpfile myfile
```






