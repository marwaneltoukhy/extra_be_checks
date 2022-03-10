# sconnect_for_sky130_magic
Setup to find connections only through n/pwell.

Usage:
 ```run_scheck top_cell [gds_file]```

Inputs:
 top_cell
 gds_file: required initially
Output:
 nowell/<top_cell>.lvs.nowell.log

Internals:
 Create 2 versions of the extracted netlist.
  Version 1 extracts well connectivity.
   Remove well connections and disconnected signals.
  Version 2 does not extract well connectivity.
   Remove disconnected signals.
 Compare with LVS.

netgen normally flattens unmatched cells which can lead to confusing results at higher levels.
To avoid this, create a file `noflatten`, that contains the name of cells not to be flattened.
Rerunning without specifing a gds_file is faster because only LVS will be run.
