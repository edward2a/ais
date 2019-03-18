# CMDB

Commonly CMDBs store information on organisation assets and structure.
This is provided via a combination of both a hierarchichal model and inter-asset relationships that can be expressed in various manners.

For this use case example, the following relationships will be considered:
  - depends-on
  - depended-by
  - peer

Each of this relationships has a particular significance.
The depends-on and depended-by establishes a hierarchical and chronological order of dependencies where an object that is depended-by needs to exist before the object that depends-on it.
The peer relationship establishes a related but not dependant party, this could be exemplfied as, for example, a scaling group.
