# ONETEP Benchmarking Outputs

There are two independent ONETEP simulations in our benchmarking suite.

Provided here are the 1 node, 16 node and 32 node examples for Iridis 5.

## Testcase 1:

This testcase uses 10 MPI ranks per node with 4 OpenMP threads per MPI rank, to populate the 40 CPUs per node on Iridis 5.

The input file is 4088.dat, listed in this directory

## Testcase 2:

This testcase uses 2 MPI ranks per node with 20 OpenMP threads per MPI rank, to populate the 40 CPUs per node on Iridis 5.

The input file is sc05_protonated_shift.dat, listed in this directory

## Result reporting:

Both testcases produce a .out file that contains the result. To score the benchmarks please report the following field:

TOTAL TIME:      4914.788s on    160 proc(s)

In the 1_node example, that line is present in 4088.out, line number 1042.

### Notes

Please see the 1_node, 16_node and 32_node directories for the scripts used to run on Iridis 5, with the outputs.

The .dat file must be present with the jobscript to be run.

The lines specifying the ONETEP exectuable and launcher paths will be filesystem and compilation dependent:

```
Point this to your ONETEP executable.
onetep_exe=\
"/home/hpc/benchmarks-2022/ONETEP/source/bin/onetep.iridis5.intel21.omp.scalapack"

Point this to your ONETEP launcher.
onetep_launcher=\
"/home/hpc/benchmarks-2022/ONETEP/source/utils/onetep_launcher"
```

Please edit these to match your compiled ONETEP location


