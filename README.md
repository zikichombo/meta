# [ZikiChombo](http://zikichombo.org) meta
This repository is mostly a placeholder reserved for cross-project code,
documentation, and cross-project [Questions](https://github.com/zikichombo/meta/issues/1).

It does not contain code intended for direct consumption, though you are welcome if 
you wish.  Rather, any code which needs to be shared for infrastructure or accross
projects can be placed here.

All documentation here is subject to change at any time, as we are just starting.  Feel free
to comment to help guide us.  Please do not rely on the documentation for planning 
until this repository using semantic versioning, and it might not.

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


# Synchronisation at heads
From time to time, cross module commits may not be synchronised.  ZikiChombo
only releases each repository independently.  We estimate the versioning and
evolution of the repositories will be very heterogenous and so brief 
desynchonisation at heads will incur less maintenance overhead.  Go's module
system will help enforce synchronisation between releases.






