# Example Compile Procedure

Below are the commands used to aquire and compile the GROMAX 2022 application. Included in this folder is a copy of the source gromacs-2022.3.tar.gz

```shell
mkdir 2022.3_mkl22

cd 2022.3_mkl22

mkdir source; cd source

wget ftp://ftp.gromacs.org/gromacs/gromacs-2022.3.tar.gz

tar -xvf gromacs-2022.3.tar.gz

cd gromacs-2022.3; mkdir build; cd build

module load intel-compilers/2022.2.0

module load intel-mpi/2021.7.0

module load intel-mkl/2022.2.0

module load python/3.9.7

module load gcc/10.3.0

CC=icx CXX=icpx cmake .. -DBUILD_SHARED_LIBS=OFF -DGMX_FFT_LIBRARY=mkl -DGMX_GPLUSPLUS_PATH=/local/software/gcc/10.3.0/bin/g++ -DCMAKE_INSTALL_PREFIX=/local/software/gromacs/2022.3_mkl22/. -DGMX_MPI=ON -DGMX_OPENMP=ON -DGMX_CYCLE_SUBCOUNTERS=ON -DGMX_GPU=OFF -DGMX_BUILD_HELP=OFF -DGMX_HWLOC=OFF -DGMX_SIMD=AVX_512 -DGMX_OPENMP_MAX_THREADS=256 -DGMXAPI=OFF -DMKL_INCLUDE_DIR="/local/software/intel/install/2022.3.0/mkl/2022.2.0/include/"

make -j 16 

make install
```