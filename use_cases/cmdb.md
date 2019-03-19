# CMDB

Commonly CMDBs store information on organisation assets and structure.
This is provided via a combination of both a hierarchichal model and inter-asset relationships that can be expressed in various manners.

For this use case example, the following relationships will be considered:
  - depends-on
  - depended-by
  - peer

Each of this relationships has a particular significance.
The depends-on and depended-by establishes a hierarchical and chronological order of dependencies where an object that is depended-by needs to exist before the object that depends-on it.
The peer relationship establishes a related but not dependency link, this could be exemplfied as, for example, a scaling group.

A CMDB has to deal with a variety of asset types which can range from physical to virtual items, along with dealing with their history throughout their lifecycle.
This means the lifecycle of an item consists of a model in the lines of the folling items:
  - item creation
  - tracking of relationships and parameter changes
  - item decommission

It is worth mentioning that when an object reaches a decommissioned stage, this must not be removed from the database, but preserved for integrity of the timeline for auditing and possibly legal purposes.
One thing can be argued though, and that is whether the timeline should be split to separate historical deprecated assets in some way that the content of the live data is not extended unnecessarilly just to keep the timeline complete.

