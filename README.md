+++++++++++++Benjamin Czaja's Orbital Integrator+++++++++++++++++++++++++
		      September 29th 2015
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Installing and compiling the integrator
======================================================================================================
Everything needed to compile and run the integrator is located in the tarfile
"ben_integrator2015.tar". Including this README. to compile the integrator run the command

make integrator2015

 to compile the integrator that accepts RA and DEC in degrees. 
 ======================================================================================================


RUNNING THE INTEGRATOR
======================================================================================================
Running the Integrator is easy. The integrator can be called by the command ./integrator2015.exe and requires 
that you pass it six arguments. 
1. inputfile (format is described below)
2. outputfile (this is where all the orbital parameters will be stored for each star)
3. galactic potential you would like to use (this is an integer 1,2,3,4,5)
    (1).................."<<"Kenyon et al. 2008"<<endl;
    (2).................."<<"Paczynski B. 1990"<<endl;
    (3).................."<<"Jonhston K. V., Spergel D. N., Hernquist 1995"<<endl;
    (4).................."<<"Dauphole B., Colin J. 1995"<<endl;
    (5).................."<<"Allen C., Santillan A. 1991"<<endl; 
  --- I recomend using option (3)
4.how many giga years you would like to trace each particle. This value is a multiple of a giga years. If you 
want to integrate each particle for a giga pass it 1. 10 giga years pass it 10.
5. The type od distance you would like to use. (0) parallax aka arcseconds or (1) parsecs.
-- I recommend arcsecs, for reasons to do with the method following coordinate transformations of Johnson and Soderblom (1987AJ.....93..864J). It is more consistant and provides better errors
6. Whether you want to propogate errors. this is either (1) for yes and (0) for no. note that running with errors will slow down 
the integration time.
======================================================================================================
EXAMPLE:

If we wnat to simulate some list of stars in a file called "input_example.dat", and output our results
to a file named "output_example.dat" using Jonhston K. V., Spergel D. N., Hernquist 1995 potential.
we will run for 10 giga years each,w ith no error propogation. We will use the command ....

./integrator2015.exe input_example.dat output_example.dat 3 10 0 0

Try this command out as "input_example.dat" was included in the tarfile.
I recomend using the coordinates in degrees. it makes life easier when you want to crossmatch with other 
astronomical surveys.

=======INPUT FOR ORBITAL INTEGRATOR "Degrees"============
===DISTANCES IN PARALLAX!!!!
If there is an unknown value, please enter in a nan.
--------------------------------------------------------------------------------
Column|.......|Units|..........|What it is
--------------------------------------------------------------------------------
  1  |........|string |..........|Starname
  2  |........|Degrees|..........|Right ascension 
  3  |........|Degrees|..........|Declination 
  4  |........|mas/yr |..........|Proper motion in right ascension
  5  |........|mas/yr |..........|Standard error of the proper motion in right ascension
  6  |........|mas/yr |..........|Proper motion in Declination
  7  |........|mas/yr |..........|Standard error of the proper motion in declination
  8  |........|mas    |..........|Parallax (from sun)
  9  |........|mas    |..........|Standard error of the parallax
  10 |........|km/s   |..........|Radial velocity
  11 |........|km/s   |..........|Standard error of the radial velocity


=======INPUT FOR ORBITAL INTEGRATOR "Degrees"============
===DISTANCES IN PARSECS!!!!
If there is an unknown value, please enter in a nan.
--------------------------------------------------------------------------------
Column|.......|Units|..........|What it is
--------------------------------------------------------------------------------
  1  |........|string |..........|Starname
  2  |........|Degrees|..........|Right ascension 
  3  |........|Degrees|..........|Declination 
  4  |........|mas/yr |..........|Proper motion in right ascension
  5  |........|mas/yr |..........|Standard error of the proper motion in right ascension
  6  |........|mas/yr |..........|Proper motion in Declination
  7  |........|mas/yr |..........|Standard error of the proper motion in declination
  8  |........|pc     |..........|Parallax (from sun)
  9  |........|pc     |..........|Standard error of the parallax
  10 |........|km/s   |..........|Radial velocity
  11 |........|km/s   |..........|Standard error of the radial velocity


========ORBITAL OUTPUT PARAMETERS FORMAT==============
Column|.................|What it is
---------------------------------------------------------------------------------------------
   1  |.................|X position KPC from galactic Center(positive toward center)
   2  |.................|Y position KPC from galactic Center(positive toward galactic rotation)
   3  |.................|Z position KPC from galactic Center(postiive toward galactic north pole)
   4  |.................|U velocity in km/s (positive toward galactic center)
   5  |.................|U_error in km/s
   6  |.................|V velocity in km/s (positive toward galactic rotation)
   7  |.................|V_error in km/s
   8  |.................|W velocity in km/s (positive toward galactic north pole)
   9  |.................|W_error in km/s
   10 |.................|Apogalacticon (Rmax) in KPC
   11 |.................|error_plus Apogalacticon (Rmax) in KPC
   12 |.................|error_minus Apogalacticon (Rmax) in KPC
   13 |.................|Perigalacticon (Rmin) in KPC
   14 |.................|error plus Perigalacticon (Rmin) in KPC
   15 |.................|error minus Perigalacticon (Rmin) in KPC
   16 |.................|Maximum Height above galactic plane in KPC
   17 |.................|error plus Maximum Height in KPC
   18 |.................|error minus Maximum Height in KPC
   19 |.................|x-comp angular momentum in 10 km kpc s^-1
   20 |.................|error plus x-comp angular momentum in 10 km kpc s^-1
   21 |.................|error minus x-comp angular momentum in 10 km kpc s^-1
   22 |.................|y-comp angular momentum in 10 km kpc s^-1
   23 |.................|error plus y-comp angular momentum in 10 km kpc s^-1
   24 |.................|error minus y-comp angular momentum in 10 km kpc s^-1
   25 |.................|z-comp angular momentum in 10 km kpc s^-1
   26 |.................|error plus z-comp angular momentum in 10 km kpc s^-1
   27 |.................|error minus z-comp angular momentum in 10 km kpc s^-1
   28 |.................|magnitude-comp of x-y angular momentum in 10 km kpc s^-1   ...... ie  (L_|_ = sqrt(Lx^2 + Ly^2))
   29 |.................|error plus magnitude-comp of x-y angular momentum in 10 km kpc s^-1
   30 |.................|error minus magnitude-comp of x-y angular momentum in 10 km kpc s^-1
   31 |.................|eccentricity
   32 |.................|error plus eccentricity 
   33 |.................|error minus eccentricity 
   34 |.................|Energy in 100 km^2 s^-2
   35 |.................|error plus in Energy in 100 km^2 s^-2
   36 |.................|error minus in Energy in 100 km^2 s^-2
   37 |.................|Period in Gyr
   38 |.................|error plus Period in Gyr
   39 |.................|error minus Period in Gyr
