# PHY2200-Portfolio-DV
This repo houses two small projects as well as the final project that I completed for PHY2200 Computational Physics.

==== Nitrous Oxide Properties Curvefitting ====


This notebook reads in data from a .txt file with data on Nitrous Oxide from ESDU91022. I initially was going to use this for simulating hybrid rocket motors at some point, and maybe I'll get to modelling some eventually, but for now this only exists to compare my curvefit results to the parameters obtained in the ESDU91022 paper. I have had an interest in developing hybrid rockets for a while but haven't looked too deeply into other resources available beyond Richard M. Newlands' "The Science and Design of the Hybrid Rocket Engine." This is also where the attempt to determine Z-factor comes into play. The Z-factor helps to "fix" the ideal gas law at lower temperatures.

==== Coulomb Potential Well Chaos ====


This project was inspired by a talk given by Tom Dooling about a system in which a charged particle constrained to move one-dimensionally oscillates in a well generated by and between two repulsive charges. One of these repulsive charges moves sinusoidally, and changing the frequency (and amplitude) leads to the system becoming chaotic at a certain point. This includes a plot of the position of the one-dimensionally moving particle over time, as well as the ability to generate phase plots of the system and even a bifurcation diagram.

==== Chaotic Pendulum Project ====


This project was my final project, and it represents one of my finest works in python. The inspiration came from a video linked in the jupyter notebook. Essentially, consider a rigid pendulum with the mass (m) a distance L from the pivot point of the pendulum.
Also consider some number of attractors in a plane a distance L below the pendulum's pivot. Each attractor has a force proportional to 1/s^2, where s is the distance the mass is to the attractor.
The system of equations was derived through the Lagrangian as a derivation through forces alone would be incredibly difficult. The drag force proportional to velocity squared was introduced after the derivation of the system of equations, and was implemented to ensure the mass would actually end up at an attractor after some finite length of time. In this program, I place the attractors in a regular polyhedra in the plane below the pivot and assign them all the same attractiveness value.
The program is able to not only plot the theta and phi position of the mass over time, but can also animate the system in xy, xz, and yz projections. Further, it attempts to replicate a plot similar to what was found in the aforementioned video. Keep in mind, generating this plot takes a significant amount of time because I did not choose to use numba given that the functions require global variables to operate in their current forms. For that, I would recommend looking at the plots included.
Note that the coordinate system defines theta to be the angle from the z-axis, and phi to be the angle from the x-axis in the x-y plane.

Here are some parameters in the program that can be changed (units in parenthesis):


N = number of attractors.


L = length of pendulum rod (m).


R = distance each attractor is from the center of the plane below the pendulum's pivot (m).


m = mass of the pendulum (kg) (at the end of the pendulum, so more akin to that of say attaching a bob to the end of the massless rod).


g = acceleration due to gravity (m/s^2).


alpha = strength of attractor. Note that a negative number means that it will attract and that positive numbers make it repulsive (N m^2/kg).


beta = drag force proportionality constant (whatever the dimensions work out to, typically just kept on the order of 1e-4 or 1e-3 as to not overdampen).


theta_0 = initial position in the theta coordinate (radians), used for individual runs.


phi_0 = initial position in the phi coordinate (radians), used for individual runs.


omega-theta_0 = initial angular velocity in the theta direction (rad/s), used for individual runs.


omega-phi_0 = initial angular velocity in the phi direction (rad/s), used for individual runs.


tend = time you want the system to run for (s).


dt = time step (s). Kept around 1e-3 for simulation accuracy's sake.


Note: the simulation spits NaN for small theta. This is just an artifact of how the system of equations was formed, given there are coordinate singularities embedded within the phi double-dot (second time derivative of phi) expression.
