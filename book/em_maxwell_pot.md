In this subsection, we derive the second-order wave equations operating on the electrical scalar potential and the magnetic vector potential.

For reference, here are Maxwell's equations:

And these are the relationships between the potentials and the force vector fields:

- **magnetic force from vector potential:** $ \vec{B} {{=}} \vec{\nabla} \times \vec{A} $
- **electric force from scalar potential:** $ \vec{E} {{=}} - \vec{\nabla} A_0 $

Equation ii is automatically satisfied by the fact that the magnetic field vector is the curl of the magnetic vector potential, because the divergence of the curl is always 0. Similarly, equation i is just the basic source equation that is easily incorporated into the second-order wave equation as we saw in the main chapter. Thus, the key challenge to explain is how the iii and iv equations correspond to simple wave equations on the potentials.

We start by inserting the definition for $\vec{B}$ into equation (iii), to get:

- $ \vec{\nabla} \times \vec{E} = - \frac{\partial \vec{B}}{\partial t} $

  
$ \vec{\nabla} \times \vec{E} = - \frac{\partial}{\partial t}\left(\vec{\nabla} \times \vec{A}\right) $

$ \vec{\nabla} \times \vec{E} = - \vec{\nabla} \times \frac{\partial \vec{A}}{\partial t} $

$ \vec{\nabla} \times \vec{E} + -\vec{\nabla} \times \frac{\partial \vec{A}}{\partial t} = 0 $

$ \vec{\nabla} \times \left(\vec{E} + \frac{\partial \vec{A}}{\partial t} \right) = 0 $

Because this quantity in the parentheses has zero curl according to this equation, it means that it can be written in terms of a gradient of a scalar potential (gradients of scalar fields can't have curl; for example, a ball rolling down a surface can only roll, not spin):

- $ \vec{E} + \frac{\partial \vec{A}}{\partial t} = - \vec{\nabla}{A_0} $

Therefore, we can just re-arrange these terms to get a definition of the electric vector field in terms of the scalar field:

- $ \vec{E} = - \vec{\nabla} A_0 - \frac{\partial \vec{A}}{\partial t} $

This definition agrees with the simple gradient equation given earlier, but it also adds the first temporal derivative of the vector potential as a contributor to the electrical field. To remove this extra term, we need to remove one extra degree of freedom from our system, by making the following definition:

- $ \frac{\partial A_0}{\partial t} = - c^2 \vec{\nabla} \cdot \vec{A}$

This is known as the **Lorenz gauge** or condition (not Lorentz, as some incorrectly state), which is also covered in the main chapter.

Now we use this within equation i and iv. For equation (i), we get:

- $ \vec{\nabla} \cdot \vec{E} = \frac{1}{\epsilon_0} \rho $

  
$ \vec{\nabla} \cdot \left( \vec{\nabla} A_0 + \frac{\partial \vec{A}}{\partial t} \right) = - \frac{1}{\epsilon_0} \rho $

$ \nabla^2 A_0 + \vec{\nabla} \cdot \frac{\partial \vec{A}}{\partial t} = - \frac{1}{\epsilon_0} \rho $

and for equation (iv), we get:

- $ \vec{\nabla} \times \vec{B} = \mu_0 \vec{J} + \mu_0 \epsilon_0 \frac{\partial \vec{E}}{\partial t} $

  
$ \vec{\nabla} \times \left( \vec{\nabla} \times \vec{A} \right) = \mu_0 \vec{J} + \mu_0 \epsilon_0 \frac{\partial}{\partial t} \left( -\vec{\nabla} A_0 - \frac{\partial \vec{A}}{\partial t} \right) $

$ \left( \nabla^2 \vec{A} - \frac{1}{c^2} \frac{\partial^2 \vec{A}}{\partial t^2} \right) - \vec{\nabla} \left( \vec{\nabla} \cdot \vec{A} + \frac{1}{c^2} \frac{\partial {A_0}}{\partial t} \right) = -\mu_0\vec{J} $

$ \Box \vec{A} - \vec{\nabla} \left( \vec{\nabla} \cdot \vec{A} + \frac{1}{c^2} \frac{\partial {A_0}}{\partial t} \right) = -\mu_0 \vec{J} $

So, perhaps you can see that now we are getting somewhat closer to a wave equation. We now have the $\nabla^2$ terms showing up in both equations, and in the latter we have a $\frac{\partial^2 {}}{\partial t^2}$ term, such that we get the classic wave equation signature, as indicated by the last line where we substituted in the d'Alembertian operator $\Box = \frac{\partial^2 {}}{\partial t^2} - \nabla^2$, which encapsulates the wave equation dynamics of second-order time minus second-order space differentials.

But these equations are still quite messy, and certainly are not purely wave equations. Furthermore, there is still some extra degree of freedom in these potentials in terms of their implications for the observable $\vec{E}$ and $\vec{B}$ fields. For example, you can add any kind of constant numerical offset to the entire electrical potential $A_0$, and this will not change the behavior of the system, because the observable electrical force is defined only in terms of the gradient or slope of this potential field, not its absolute magnitude.

In more formal parlance, it is said that one can choose different {\em gauges} for these potentials, and this choice will affect the form of the equations. In the Lorenz gauge mentioned earlier, this extra degree of freedom is removed by defining:

- $ \frac{\partial {A_0}}{\partial t} = - c^2 \vec{\nabla} \cdot \vec{A}$

For later convenience, this also means that:

- $ \vec{\nabla} \cdot \vec{A} = - \frac{1}{c^2}\frac{\partial {A_0}}{\partial t} $

When you take this latter form and plug it into the above two Maxwell equations, you end up canceling some of the nasty bits out, and you get a very nice form of standard wave equations. For equation (i), we get:

- $ \nabla^2 A_0 + \vec{\nabla} \cdot \frac{\partial {\vec{A}}{\partial t}} = - \frac{1}{\epsilon_0} \rho $

  
$ \nabla^2 A_0 + \frac{\partial {}}{\partial t}\left(\vec{\nabla} \cdot \vec{A}\right) = - \frac{1}{\epsilon_0} \rho $

$ \nabla^2 A_0 - \frac{\partial {}}{\partial t}\left(\frac{1}{c^2}\frac{\partial {A_0}}{\partial t}\right) = - \frac{1}{\epsilon_0} \rho $

$ \nabla^2 A_0 - \frac{1}{c^2} \frac{\partial^2 {A_0}}{\partial t^2} = - \frac{1}{\epsilon_0} \rho $

$ \frac{\partial^2 {A_0}}{\partial t^2} = c^2 \nabla^2 A_0 + \frac{1}{\epsilon_0} \rho $

(where the boxes indicate the location of the substitution). The result is clearly a basic wave equation with an additional \`\`driving'' term of $\frac{1}{\epsilon_0} \rho$.

For equation (iv), you get:

- $ \left( \nabla^2 \vec{A} - \frac{1}{c^2} \frac{\partial^2 \vec{A}}{\partial t^2} \right) - \vec{\nabla} \left( \vec{\nabla} \cdot \vec{A} + \frac{1}{c^2} \frac{\partial {A_0}}{\partial t} \right) = -\mu_0\vec{J} $

  
$ \left( \nabla^2 \vec{A} - \frac{1}{c^2} \frac{\partial^2 \vec{A}}{\partial t^2} \right) - \vec{\nabla} \left( \vec{\nabla} \cdot \vec{A} - \frac{1}{c^2}c^2 \vec{\nabla} \cdot \vec{A} \right) = -\mu_0\vec{J} $

$ \left( \nabla^2 \vec{A} - \frac{1}{c^2} \frac{\partial^2 \vec{A}}{\partial t^2} \right) - \vec{\nabla} \left( \vec{\nabla} \cdot \vec{A} - \vec{\nabla} \cdot \vec{A} \right) = -\mu_0\vec{J} $

$ \nabla^2 \vec{A} - \frac{1}{c^2} \frac{\partial^2 \vec{A}}{\partial t^2} = -\mu_0\vec{J} $

$ \frac{\partial^2 \vec{A}}{\partial t^2} = c^2 \nabla^2 \vec{A} + \mu_0\vec{J} $

Again, somewhat miraculously, a wave equation emerges, again with a driving term.</text>
