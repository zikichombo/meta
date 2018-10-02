# [ZikiChombo](http://zikichombo.org) meta
This repository is mostly a placeholder reserved for cross-project code,
documentation, and cross-project [Questions](https://github.com/zikichombo/meta/issues/1).

It does not contain code intended for direct consumption, though you are welcome if 
you wish.  Rather, any code which needs to be shared for infrastructure or accross
projects can be placed here.

All documentation here is subject to change at any time, as we are just starting.  Feel free
to comment to help guide us.  Please do not rely on the documentation for planning 
until this repository is using semantic versioning, and it might not.

# Special Thanks
ZikiChombo would like to thank especially the following Go sound/audio related projects
(sorted alphabetically by common name).
1. azul3d.org
1. github.com/yobert/alsa
1. github.com/rakyll/audio
1. github.com/faiface/beep
1. dasa.cc/snd
1. github.com/mewkiz/flac
1. github.com/go-audio
1. github.com/hajimehoshi/go-mp3
1. github.com/padster/go-sound
1. bitbucket.org/bcmills/harmonolog
1. github.com/hajimehoshi/go-mp3
1. github.com/jfreymuth/oggvorbis
1. github.com/hajimehoshi/oto
1. github.com/gordonklaus/portaudio
1. github.com/nf/sigourney

Please give them a star, try them out too. We're all working together and
learning from each other.  Ideas to add to the list?  Give us a shout, we'd
like to learn from as many projects as possible.

# Semantic Versioning
ZikiChombo uses semantic versioning for source code repositories intended for direct
use.  Our pre-release notation is as follows, with W a positive integer.

1. Alpha pre-releases should be vX.Y.Z-alpha.W
1. Beta pre-releases should be vX.Y.Z-beta.W
1. Release candidates should be vX.Y.Z-rc.W
1. Releases should be plain ole vX.Y.Z

The semantic version should apply to the least reliable component or aspect of the respective
repository.

Alpha code is highly volatile or potentially highly volatile.

We _speculate_ beta code is not volatile but maybe a little rough around the edges.

Release candidate code represents final iterations with consumers carrying 
risk associated with using ZikiChombo. 

As some repositories do not have known consumers carrying risk, some versions
can jump from beta to releases without going through "-rc" pre-releases.  
If you would like to see "-rc" pre-releases please let us know.  At the time of 
this writing, no zc repositories have -rc pre-releases planned.

If a zc module `A` depends on another zc module `B` in terms of imports, then 
`A` must not have a tag which is more reliable than `B` in terms of pre-release
notation. Note that dependencies in terms of imports is not the same thing 
as projected dependencies based on module roadmap.

## Alpha/Beta stickiness and monotonicity
Since pre-releases are characterised by the least reliable component,
and it can be that the rest of the code needs patch release or minor
version bumps, it is possible, even probable early on, that we will bump 
minor and patch release versions without reaching a full release.  When
this occurs we will enforce that no backwards motion occurs with respect
to alpha-ness or beta-ness or rc-ness.  So we can have

```
    v0.1.2-alpha.W
    v0.2.0-alpha.W
```

or 

```
    v0.1.2-alpha.W
    v0.1.3-alpha.W
```

but not 

```
    v0.1.2-alpha.2
    v0.1.3-alpha.1
```

and also not

```
    v0.1.2-beta.1
    v0.1.3-alpha.1
```

Once pre-release tags disappear and there is a full release, this monotonicity 
resets and we can go back to the state of low alpha quality and corresponding
faster forward motion.

## Preleases and ext
the ext module has no prerelease notation to accomodate collaborations at 
different stages of stability.  Use at your own risk.


# Synchronisation at heads and go get.
From time to time, cross module master heads may not be synchronised.
ZikiChombo only releases each repository independently.  We estimate the
versioning and evolution of the repositories will be very heterogenous and so
(initially) brief desynchonisation at heads will incur less maintenance
overhead than putting everything in one repository. Go's module system will
help enforce synchronisation between releases.  As Go's modules are currently
[opt-in](https://golang.org/cmd/go/#hdr-Preliminary_module_support), and only
default in the next major release, we encourage developers to opt-in to go's
modules when working with zc code.  This may become a necessity in the very
short term.  Due to the very limited nature of go get support with modules
we recommend

1. Turning off modules and setting GOPATH for go get.
1. If go get fails to build, run go get -d for download only
1. After go get succeeds via one of the above, turn modules on
while working with ZikiChombo modules. 

For example, if you want to work with ZikiChombo code in an isolated
environment under some directory D, then

```
cd D
mkdir src
GOPATH=`pwd` GO111MODULE=off go get -d zikichombo.org/P/...  # with P a project
```

should work to download the code in a dedicated workspace with root D.

Then, set GO111MODULE=on to build, test, hack, etc in D.

# build tags
We use the build tag "listen" for tests which generate or capture audio,
and for tests which generate files whose only use is listening.

By default, listen is off and you have to turn it on for testing:
```
go test zikichombo.org/xyz/ -tags listen
```

# zc+3p imports
In an effort to more effectively collaborate
we are experimenting with a repository hosted at 
github.com/zikichombo/ext

The idea is that for any collaborator that is interested in working with zikichombo
but may not want to move their project or import zc, zc and these collaborators can work here
on the part of the code that imports both.

As a result, Zikichombo makes no guarantees about licensing in ext via 
imports beyond granting its standard license to all zc contributed code in 
ext.



