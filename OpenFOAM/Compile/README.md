# Example Compile Procedure

The [OpenFoam website](https://openfoam.org/download/10-source/) has good documentation for building the software from source but below is the procedure we used.

```shell
#Start by creating a directory where you want to build OF, and cd to it. Once in that directory, download the source distributions:
wget -O - http://dl.openfoam.org/source/10 | tar xvz
wget -O - http://dl.openfoam.org/third-party/10 | tar xvz

#Rename the resulting directories:
mv OpenFOAM-10-version-10 OpenFOAM-10
mv ThirdParty-10-version-10 ThirdParty-10

cd into OpenFOAM-10/etc and edit the bashrc file:
cd OpenFOAM-10/etc
vi bashrc

#In bashrc add these two lines (I put them below this line -- export WM_PROJECT_VERSION=10)
module load cmake/3.24.1
module load openmpi/4.1.4/gcc

#Source the bashrc file
source bashrc

#Go into ThirdParty-10 and build the binaries:
cd ../../ThirdParty-10
./Allwmake

#Now go into OpenFOAM-10 and build the binaries:
cd ../OpenFOAM-10
./Allwmake -j

#If this is successful, then you can go to your home directory and do the following to verify the build

cd 
mkdir -p $FOAM_RUN
cd $FOAM_RUN
cp -r $FOAM_TUTORIALS/incompressible/simpleFoam/pitzDaily .
cd pitzDaily
blockMesh
simpleFoam
```