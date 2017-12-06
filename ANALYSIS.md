About GSI and work organization
===============================

A few words about computer system in GSI. There are three systems: GSI machines, Kronos machines (interface for HPC farm) and the HPC farm itself (you have no direct access there). And there are two storage systems: home and luster. GSI and Kronos have access to home, Kronos and Lustre have access to lustre, GSI has no access to lustre and HPC has no access to home. Only GSI and Kronos have access to the internet.

Home is a place where you should store your simulation and analysis code (you can access it from GSI and Cronos) but you should install all executables and sim/data on lustre (that kronos and HPC have access there).
