# tagf

`tagf` - tag files and directories

## Synopsis

    tagf TAG[ TAG2]... FILE[ FILE2]...
    tagf grep [OPTIONS...] TAG[ TAG2]...

## Description

`tagf` is a simple tool that enables associating tags with arbitrary files and directories. It also enables searching those tags.

Tags are stored in plain text files, one tag per line. The name of the tags file is identical to that of the the tagged file, but in a directory named `~/.file-tags`. For example, the tag file for `/home/user/music/song.mp3` will be `/home/user/.file-tags/home/user/music/song.mp3`. Directories are similar: the tag file for `/home/user/music` will be `/home/user/.file-tags/home/user/music:tags`.

## Dependencies

- ruby
- grep
- xargs

## Installation

0. Clone the repository: https://github.com/rmavis/tagf.
1. Move the executable `tagf` (or make a symlink to it) somewhere in your $PATH.
2. Ensure the executable is executable (`chmod` it 744, etc).
3. There is no step 3.

## Usage

To add tags to files, the pattern is:

    $ tagf TAG[ TAG2]... FILE[ FILE2]...

Tags must be specified before files. All tags will be applied to all files following the cascade of their appearance. So this:

    $ tagf ok file1 great file2

will tag `file1` with "ok" and `file2` with "ok" and "great".

By default, the given tags will be added to the given files. Tags will not be duplicated. To make the addition explicit, you can prefix tags with a `+`.

To remove a tag, prefix it with a `-`, like so:

    $ tagf -great file2

Thus, `tagf` has only two operations: adding and removing tags, and searching those tags. The form for searching is:

    $ tagf grep TAG[ TAG2]...

This will print paths of matching files to stdout, with the tag tree root (`/home/user/.file-tags`) removed, like so:

    $ tagf grep ok 
    /home/user/path/to/file1
    /home/user/path/to/file2

Searches will be case-insensitive but must match the full tag text---"o" will not match "ok", but "OK" will. If more than one tag is given, only files containing every tag will match.

### Examples

Tag all your email from your mom "email" and "mom":

    $ grep -rl "Love, Mom" ~/mail | tagf email mom

Search for those files:

    $ tagf grep mom email
    
Make a playlist of good music:

    $ tagf good music ~/music/band/album/*mp3
    $ tagf grep good music | sort > good-playlist.m3u

Look at some art:

    $ tagf art ~/pictures/*okeefe* ~/pictures/*kandinsky*
    $ tagf grep art | sxiv -
