# Example Inputs and Outputs

This benchmark uses the HPC_motorbike example repository that is available on the web at the follwing location:
https://develop.openfoam.com/committees/hpc/-/tree/develop/HPC_motorbike
The repository provides the input data for three cases, small, medium and large. We require only the large case to be run. 

To run the Large case with OpenFOAM v10 run the scripts AllmeshL and Allrun in the following v8 location/directory:
https://develop.openfoam.com/committees/hpc/-/tree/develop/HPC_motorbike/Large/v8

To run this case, a SLURM job script is added to the case directory (the following example is for 40 processors on one compute node). The output from this run can be found in large-40.out and the time required for the benchamnrk result is the real time output found on **line 77** *135m59.644s* which then needs to be converted seconds.

```shell
#!/bin/bash

#SBATCH --job-name=motorbike
#SBATCH --partition=scavenger
#SBATCH --nodes=1
#SBATCH --tasks-per-node=40
#SBATCH --time=2:00:00

source /home/hpc/benchmarks-2022/OpenFOAM/10/OpenFOAM-10/etc/bashrc
cd /home/hpc/benchmarks-2022/hpc-develop/HPC_motorbike/Large/v8
time ./AllmeshL
time ./Allrun


As you can see, both scripts were run & timed:
AllmeshL -- Pre-processing
Allrun -- Computation
```