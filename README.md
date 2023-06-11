# Numerical Simulation of Projectile Motion: Exploring Trajectories and Dynamics with Euler Method

Kaelyn Isaac Parris  

kaelyn_parris@protonmail.com

June 10, 2023

## Abstract

This article presents a numerical simulation of projectile motion using Newton's laws. The simulation investigates projectile motion with and without air resistance. Using the Euler method for numerical integration, the trajectory, range, maximum height, and time of flight of projectiles are analyzed under various launch conditions. The simulation results are visualized, accompanied by graphs of dynamical variables, facilitating a comprehensive understanding of the projectile's behavior throughout its motion.

## Outline

1. Introduction

   - Background on projectile motion
   - Importance of numerical simulations in studying projectile motion

2. Theoretical Framework

   - Overview of Newton's laws of motion
   - Introduction to numerical integration methods
     - Euler method
     - Brief mention of other integration methods

3. Simulation Setup

   - Description of the simulation parameters
   - Implementation details
     - Handling air resistance/drag forces
     - Initialization of projectile properties (position, velocity, etc.)

4. Simulation Results and Analysis

   - Exploration of projectile motion without air resistance
     - Trajectory analysis
     - Range, maximum height, and time of flight calculations
   - Incorporation of air resistance and its effects on projectile motion
     - Discussion of drag force model used
     - Analysis of changes in trajectory, range, maximum height, and time of flight
     - Comparison with results from the previous section

5. Visualization and Interpretation of Results

   - Presentation of graphs and plots showcasing the simulation data
   - Interpretation of the observed patterns and behaviors
   - Discussion on the practical implications of the findings

6. Conclusion

   - Summary of the simulation study
   - Key insights gained from the results
   - Limitations and future directions
   - Final remarks

7. References (citations to relevant sources)

## **Introduction**

### **Background on projectile motion**

When an object is given an initial velocity and is affected by gravitational acceleration and air resistance, it follows a specific path known as projectile motion. Athletes often perform this type of movement in sports like baseball, football, and shooting. The trajectory of a projectile is the path it takes while in motion.

To analyze projectile motion, an idealized model is often used. This model assumes that the projectile is a particle with constant acceleration due to gravity, disregarding factors like air resistance, earth's curvature, and rotation. While this model has limitations, it still provides valuable insights into projectile motion.

Projectile motion occurs in a vertical plane defined by the initial velocity's direction. Gravity purely affects the projectile's motion in the vertical direction, restricting it to two dimensions. The xy-coordinate plane is where the motion occurs, with the x-axis horizontal and the y-axis vertical. This results in a parabolic trajectory.

![parabolic](images/parabolic_path.png)

The key to analyzing projectile motion is treating the horizontal and vertical coordinates as separate components. The horizontal and vertical motions are independent, with the former having a constant velocity and the latter experiencing a constant downward acceleration of -g (where g is positive in the chosen coordinate system). By treating the motion as a combination of the two components, we can express the projectile's position, velocity, and acceleration as separate equations for the horizontal and vertical motions.

This is an example of the independence of perpendicular motion. An object dropped from rest will reach the ground at the same time as an object thrown horizontally from the same height.

![independence](images/independence.png)

Since the acceleration is constant we can use the kinematic equations. 

### **The Kinematic Equations**

In this case the acceleration is -g in the y-direction and 0 in the x-direction. The kinematic equations in terms of x are:

$x(t) = x_0 + v_{x0}t + \frac{1}{2}a_xt^2$

$v_x(t) = v_{x0} + a_xt$

$v_x^2 = v_{x0}^2 + 2a_x(x-x_0)$

$v_x = \frac{x-x_0}{t}$


#### **Let's break down each equation.**

Due to the independence of perpendicular motion, changing components simply requires changing the subscript and x to y.

1. Displacement:
   - $x(t) = x_0 + v_{x0}t + \frac{1}{2}a_xt^2$
   - This equation relates the displacement (x) of an object to its initial velocity (v_i_x), time (t), and acceleration (a_x).

2. Final Velocity:
   - $v_x(t) = v_{x0} + a_xt$
   - This equation relates the final velocity (v_f_x) of an object to its initial velocity (v_i_x), time (t), and acceleration (a_x).

3. Velocity Squared:
   - $v_x^2 = v_{x0}^2 + 2a_x(x-x_0)$
   - This equation calculates the velocity squared (v_x^2) of an object by adding the initial velocity squared (v_i_x^2) to twice the acceleration (a_x) multiplied by the displacement (x-x_0).

4. Velocity:
   - $v_x = \frac{x-x_0}{t}$
   - This equation calculates the velocity (v_x) of an object by dividing the displacement (x-x_0) by the time (t) taken.

These equations are fundamental in analyzing the motion of objects under constant acceleration. They allow us to determine various quantities such as displacement, velocity, acceleration, and time in a given scenario.

In this case, we are interested in the motion of a projectile. We can use these equations to determine the projectile's position, velocity, and acceleration in the x and y directions.

Appying the equations to our projectile motion scenario, we get the following:

1. Horizontal motion:
   - Displacement in the x-direction: 
     - $x = x_0 + v_{0x} t$
   - Velocity in the x-direction:
     - $v_x = v_{0x}$
   - Acceleration in the x-direction:
     - $a_x = 0$

2. Vertical motion:
   - Displacement in the y-direction:
     - $y = y_0 + v_{0y} t - \frac{1}{2} g t^2$
   - Velocity in the y-direction:
     - $v_y = v_{0y} - g t$
   - Acceleration in the y-direction:
     - $a_y = -g$

From these core kinematic equations we can derive other useful equations for projectile motion.

#### **Maximum height**

The maximum height is reached when the vertical velocity is zero. Therefore, we can set the vertical velocity to zero and solve for t. This gives us the time at which the projectile reaches its maximum height.

$v_y = v_{0y} - g t$

$0 = v_{0y} - g t$

$t = \frac{v_{0y}}{g}$

Substituting this value of t into the equation for vertical displacement gives us the maximum height.

$y = y_0 + v_{0y} \frac{v_{0y}}{g} - \frac{1}{2} g \frac{v_{0y}^2}{g^2}$

$y = y_0 + \frac{v_{0y}^2}{g} - \frac{v_{0y}^2}{2g}$

$y = y_0 + \frac{v_{0y}^2}{2g}$

Therefore, the maximum height reached by the projectile is given by:

$y_{max} = y_0 + \frac{1}{2} \frac{v_{0y}^2}{g}$

#### **Time of Flight:**

The time of flight, T, is defined as the time taken by the projectile to reach the ground. This time is given by:

$T = \frac{2v₀ sin(θ)}{g}$

where:
- v₀ is the initial velocity of the projectile
- θ is the launch angle
- g is the acceleration due to gravity

Deriving the time of flight is a simple matter of finding the time at which the projectile hits the ground. This can be done by setting the vertical displacement to zero and solving for t.

$y = y₀ + v₀ sin(θ) t - \frac{1}{2} g t²$

$0 = y₀ + v₀ sin(θ) t - \frac{1}{2} g t²$

$0 = t (v₀ sin(θ) - \frac{1}{2} g t)$

$t = 0$

$v₀ sin(θ) - \frac{1}{2} g t = 0$

$t = \frac{2 v₀ sin(θ)}{g}$

$T = \frac{2 v₀ sin(θ)}{g}$

#### **Range:**

The range in projectile motion refers to the horizontal distance traveled by the projectile before it lands back on the same level as its initial launch point.

The range, R, in projectile motion is given by:

$R = \frac{v₀² sin(2θ)}{g}$


where:
- v₀ is the initial velocity of the projectile
- θ is the launch angle
- g is the acceleration due to gravity

The derivation for the range is as follows:

$R = v₀ cos(θ) t$

$R = v₀ cos(θ) \frac{2v₀ sin(θ)}{g}$

$R = \frac{2v₀² sin(θ) cos(θ)}{g}$

$R = \frac{v₀² sin(2θ)}{g}$

#### **Maximum Height:**

The maximum height in projectile motion represents the highest point reached by the projectile in its trajectory.

The maximum height, H_max, reached by the projectile is given by:

$H_{max} = \frac{v₀² sin²(θ)}{(2g)}$


where:
- v₀ is the initial velocity of the projectile
- θ is the launch angle
- g is the acceleration due to gravity

The derivation for maximum height is as follows:

$H_{max} = v₀ sin(θ) t - \frac{1}{2} g t²$

$H_{max} = v₀ sin(θ) \frac{2v₀ sin(θ)}{g} - \frac{1}{2} g (\frac{2v₀ sin(θ)}{g})²$

$H_{max} = \frac{2v₀² sin²(θ)}{g} - \frac{4v₀² sin²(θ)}{g}$

$H_{max} = \frac{v₀² sin²(θ)}{(2g)}$

### Importance of numerical simulations in studying projectile motion

Projectile motion is often taught as a fundamental concept in physics education to help students learn about motion and gravity. This involves launching objects into the air and observing their curved paths, which gravity influences solely. However, projectile motion can become more complex when it comes to realistic calculations.

One of the main challenges with projectile motion is the absence of a straightforward analytical solution. Projectile motion lacks a closed-form solution Unlike other problems with precise equations describing position, velocity, and acceleration as time functions. This is due to the inclusion of air resistance, which significantly impacts the object's trajectory.

When air resistance cannot be ignored, calculating the trajectory becomes more challenging because the effects of air resistance are velocity-dependent. As a result, the acceleration is no longer constant. 

To accurately model and predict projectile motion, computer simulations are essential. Simulations use numerical integration methods to solve the equations of motion, accounting for gravity, air resistance, and other relevant forces. Simulations provide a step-by-step approximation of the projectile's motion by discretizing time and iteratively updating the object's position and velocity.

Simulations have several advantages when dealing with the complexities of realistic projectile motion. They allow for incorporating intricate mathematical models that consider the changing effects of air resistance as the object moves through the air. Additionally, simulations provide a flexible framework for exploring different scenarios by adjusting launch angles, initial velocities, and environmental conditions.

Visualizations provided by simulations enhance the understanding of projectile behavior. Dynamic plots of trajectory, velocity, and other relevant quantities over time show how factors like air resistance impact the projectile's path. This visual feedback fosters a comprehensive comprehension of the complex behavior exhibited by projectiles.

Simulations can also encompass more complex scenarios involving multiple projectiles or interactions with obstacles, allowing for exploring various strategies, such as optimizing launch parameters to achieve specific objectives like maximum range or height.

## Theoretical Framework

### Overview of Newton's Laws of Motion
Newton's laws of motion provide a fundamental framework for understanding the motion of objects. These laws, formulated by Sir Isaac Newton in the 17th century, describe the relationship between the motion of an object and the forces acting upon it. The three laws are:

1. **Newton's First Law (Law of Inertia):** An object at rest will remain at rest, and an object in motion will continue in motion with constant velocity unless acted upon by an external force.

2. **Newton's Second Law (Law of Acceleration):** The acceleration of an object is directly proportional to the net force applied to it and inversely proportional to its mass.

3. **Newton's Third Law (Law of Action-Reaction):** For every force there is an force paired with it that is equal in magnitude and opposite in direction.

Understanding Newton's laws of motion is crucial for analyzing the behavior of projectiles and predicting their trajectories under the influence of external forces such as gravity and air resistance.

### Introduction to Numerical Integration Methods
Numerical integration methods play a vital role in simulating and analyzing projectile motion. These methods provide a means to approximate the behavior of objects by discretizing time and numerically calculating their positions, velocities, and accelerations at discrete time intervals.

#### Euler Method
One commonly used numerical integration method is the Euler method. It is a straightforward approach that approximates the derivative of a function using finite differences. In the context of projectile motion, the Euler method can be employed to numerically integrate the equations of motion and determine the trajectory of the projectile.

The Euler method involves dividing the time interval into small steps and updating the position and velocity of the projectile based on the current values and the calculated acceleration at each time step. While the Euler method is relatively simple to implement, it has some limitations, such as accumulating error over long integration periods and being sensitive to step size.

#### Brief Mention of Other Integration Methods
In addition to the Euler method, various other numerical integration methods exist, offering different levels of accuracy and stability. Some commonly used integration methods in the context of projectile motion include:

- **Runge-Kutta Methods:** These are a family of numerical integration methods that provide higher accuracy compared to the Euler method by considering multiple intermediate steps. The fourth-order Runge-Kutta (RK4) method is particularly popular for its balance between accuracy and computational efficiency.

- **Verlet Integration:** Verlet integration is a symplectic integration method commonly used for simulating conservative systems. It can be advantageous in certain cases where energy conservation is important.

- **Adaptive Integration Methods:** These methods dynamically adjust the step size during the integration process to maintain a desired level of accuracy. Adaptive integration can help mitigate error accumulation and improve the efficiency of simulations.

## Simulation Setup

## Simulation Results And Analysis

## Visualization And Interpretation Of Results

## Conclusion

## References

* Thornton, Stephen T., and Jerry B. Marion. Classical Dynamics of Particles and Systems. 5th ed. Belmont, CA: Brooks/Cole, 2004.
* Young, Hugh D., Roger A. Freedman, and Hugh D. Young. University Physics with Modern Physics. 15th edition. Hoboken, N.J: Pearson Higher Education, 2020.
* Holley, Adam. "Computational Physics." PHYS 4130. Tennessee Technological University, Fall 2022.
* LibreTexts. "Projectile Motion." Accessed June 10, 2023. https://phys.libretexts.org/Bookshelves/University_Physics/Book%3A_Physics_(Boundless)/3%3A_Two-Dimensional_Kinematics/3.3%3A_Projectile_Motion.
