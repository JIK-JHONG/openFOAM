# Install

You can download from [OpenFOAM](https://www.openfoam.com) or download form [Github](https://github.com/gerlero/openfoam-app) which package as APP

# Change the path for script (simulation project)

export FOAM_RUN=<Your_Path>/openFOAM

**It will be changed to <Your_Path>**

# Copy the tutorials to your <floder_path>

@floder_path

**cp -r $FOAM_TUTORIALS/<tutorials_path> .**


# Complie & Run

I have written the bash such as Allrun / Allclean to run the script.

**MacOS**

./Allrun 

./Allclean

# Review the Result

You need to install the [paraView](https://www.paraview.org) first.

brew 

**brew install --cask paraview**

run paraView for check results

paraView


Simulation for 2 inlets of air in the tank.
-
1. model 

![Intro_Img_Grid](https://github.com/JIK-JHONG/openFOAM/blob/main/Image_Intro_openFOAM_0.jpeg)

//     4-----5      z+|
//   7/|   6/|        |   
//   | 0---|-1        o-----
//   | /   | /       /     x+
//   3-----2      y-/  
//                      

0    (0 0 0)
1    (20 0 0)
2    (20 1 0)
3    (0 1 0)
4    (0 0 50)
5    (20 0 50)
6    (20 1 50)
7    (0 1 50)

| air      |
|----------|
|          |
| water    |
|          |
|          |
|__A____A__|

"A"s are the inlets for inputung the air

walls
    {
        type wall;
        faces
        (
            (0 1 2 3)
            (1 2 6 5)
            (0 3 7 4)
        );
    }
    frontAndBack
    {
        type empty;
        faces
        (
            (0 1 5 4)
            (3 2 6 7)
        );
    }
    atmosphere
    {
        type patch;
        faces
        (
            (4 5 6 7)
        );
    }
