# Introduction to Waves

- The project file: [wave_intro.proj](Media:wave_intro.proj "wikilink") (click and Save As to download, then open in [EmeWave](EmeWave "wikilink"))

Back to [WELDBook/Sims/All](WELDBook/Sims/All "wikilink") or [Waves Chapter](WELDBook/Waves "wikilink").

# Project Documentation

This simulation brings to (simulated) life the properties of waves, using the second-order wave equation in a regular Cellular-Automaton (CA) like grid of cells across space, as developed in the [Waves Chapter](WELDBook/Waves "wikilink"). We begin with a one-dimensional version where all the code is available to be examined and modified, and then move to the full 3D simulation provided by [EmeWave](EmeWave "wikilink"). This project also serves as an introduction for how to use the software.

## One Dimensional Wave Packet

To begin, we examine a simple one-dimensional (1D) version of the wave simulation. Go to the program, which is a self-contained complete simulation of this 1D case. First, let's just see some phenomenology from running it, and then we'll see in detail how it works. A contains a gui-based programming system that generates C-like script code that is then executed. It has variables, arguments for calling from other programs, local objects (obis), and code that is run during initialization (init_code), and the main prog_code to be run. You should see the overall control panel view of the OneDWaves program, in the middle of the 3 panels visible in the main window.

These wave packets are moving at the speed of light (one state cell per unit time), and we'll see in the next chapter that they have many of the properties of light waves (electromagnetic (EM) radiation).

As the waves propagate toward the fixed edges of the state space, they bump up against them and bounce off, after only half of the wave packet has hit up against this "wall", and reflect back in the opposite direction. Fascinating already!

This time, you can see these two wave packets **superpose** right through each other -- this ability of waves to support *linear superpositions* of states is essential for explaining many features of both EM and quantum mechanics (QM). Indeed, the very fact that matter can exhibit this superposition property would seem to be sufficient to motivate a purely wave-based model -- how can hard little particles possibly superpose in the way that waves so naturally do?

After watching the amazing superposition process unfold, where the waves merge into one (and almost disappear at one point), we can now start to understand in greater detail what is going on. You can also the simulation and use the single-stepping button to watch the waves superpose step-by-step, to see how nearly completely the waves dissolve at various points -- it seems to defy the imagination that such a state could contain latent within it the full structure of these two separate wave packets. This should give you a deep appreciation for the often surprising and counter-intuitive nature of waves.

## The Wave Equations

Now let's examine the program code that is creating this amazing behavior. It is dead simple.

\<pre\>

## These are the Wave Equations!

neigh_sum = neigh_l + neigh_r // average of my neighbor values force = neigh_sum - 2.0 \* cur; // restoring force = restoring force = neighbors vs. my state value acc = c_sq \* force; // acceleration = force, and speed of light acts as a kind of mass-like term in f=ma; a = f/m new_vel = vel + acc; // new velocity = current velocity + new acceleration new_state = cur + new_vel; // new state value = current + new velocity \</pre\>

As discussed in the [Waves Chapter](WELDBook/Waves "wikilink"), each state value is being driven by the difference between the neighbor states and the current state value, which acts as a force that creates an acceleration, which then drives changes in the velocity of that state, finally causing changes in the state value itself. This is all very basic Newtonian physics if we think of the state experiencing a force imposed by the neighboring states. That such a simple set of equations produces the beautiful, often bewildering behavior of waves is nothing short of amazing. That this basic dynamic, with suitable extensions, will carry us all the way to a potentially complete description of electrodynamics is nothing short of astounding!

You should see that the green (acceleration) curve has become essentially a mirror-image reflection of the line -- this shows that the forces at work are pulling in the states back in the opposite direction -- the essential feature of wave dynamics is this "restoring" tension that tries always to pull the extreme values back into the fold. This is the effect of the neighbors always pulling you back toward their average value. If you stand out, you'll get pulled back.

If this restoring force directly updated the cur state value, then you end up with a diffusion equation, where disturbances quickly dissipate into nothingness -- the neighbors end up quashing all the exceptions and everything levels out to a uniform state. However, because this restoring force drives a velocity, the wave states always end up overshooting their neighbor's values. As they get pulled back down, they accelerate further, and zoom past their neighbors, going extreme on the other side. Because there is *no friction* or other loss of energy in this system, the disturbances are perfectly preserved, and this propagation of over and under-shooting just keeps going on and on.

You should be able to track how the accelerations drive the velocities drive the states. As the wave packets separate out, the whole system stabilizes completely, with the packets just moving steadily one grid state at a time, but the acceleration, velocity, and state all maintain the same relationship. You should see that this relationship is as follows:

- acceleration is completely out of phase with the state value -- it is maximal where states are minimal, and vice-versa
- velocity is intermediate between acceleration and state -- it is maximal at the half-way point between the peaks of these other values.

Thus, the velocity is greatest just as you're screaming past your neighbors on the way to the other extreme state value.

All of this can also be understood in terms of a pendulum, e.g., picture yourself on a swing. The restoring force (gravity in this case) is greatest when you are at the height of your swing, at the point of reversing direction from going up to going back down again. The velocity is the greatest when you are at the lowest point in the swing arc -- you've just accelerated as much as possible on the downward part of the swing, and are just about to start decelerating on your way back up.

Feel free at this point to explore the different parameters for the width, wavelength, and phase of the wave packet. If you turn on the button, it uses a hard-coded version of the same code to update the states, so it runs faster (the graph update is still somewhat slow, so that is the rate-limiting factor).

## Bound States

Next, we examine how waves behave if they completely fill the available space between two fixed points -- these are called *bound states* in quantum mechanics, and they play a critical role in understanding atomic systems, where electron waves are effectively trapped within the potential well created by the positive nuclear charge.

You should now see two full cycles of a sine wave, and when it runs, it just oscillates in place with no net lateral motion of the peaks or zero-crossing points of the state values. Although the system is in constant motion at one level, at another level it is perfectly stable -- the configuration of the waves never changes. It is this stability that makes atomic systems stable, and this was the key insight that emerged in the early days of quantum physics: atomic systems are quantized because the only stable configuration of waves are those that fit **with an integer number of wavelengths** within the atomic potential well. Indeed, according to the WELD approach, this integer quantization of waves in a bound state is the *only* thing in quantum mechanics that is actually quantized in a discrete way like this.

To truly appreciate the stability of this integer fit, you have to compare it with the alternative.

You should observe an ungainly, unstable contortion of waves that simply do not fit within the fixed space, and thus continue to wriggle around all the time.

In the real atomic system, energy will be emitted until the wavelength of the electron(s) has an integral fit within the atomic potential well, at which point it will become stable and not change further (unless perturbed by other incoming energy from the EM field). Thus, the quantized integral state represents a stable *attractor* state that the system will naturally settle into.

## Energy

Our last step in exploring the one-dimensional waves is to see what happens to the energy over time. First, we can look at the behavior of the total energy for both the bound waves and the wave packets.

You should observe something a bit surprising: the total energy plotted in the black line is *not* constant over time, and instead oscillates with the wave oscillation of the system. The total energy averaged over a long time period is completely fixed and constant, but the nature of the local wave configuration can alter the computed value locally in time. Next let's see how this looks for wave packets.

You should observe the same general phenomenon: the total energy varies over time -- it is perfectly stable when the two wave packets are moving separately, but it gets modulated when they superpose and when they hit the walls. Interestingly, the shape of the energy function over time looks just like a wave packet itself!

Perhaps you are suspicious that there might be some kind of programming error at this point. To confirm that our equation works very well for a single moving point (truly equivalent to the simple harmonic oscillator), we can shrink the system down to only 3 state values, with the two end ones fixed and only the middle one moving.

You will see a perfectly straight flat line for the total energy, and if you go back to the StateSpace1D graph, you can see a line oscillating up and down very quickly. What happens if we slow this system down a bit?

Now you should be able to see the oscillations in the kinetic () and potential () energy associated with the one active cell, and the total energy is almost perfectly constant (it has a tiny amount of variability due to numerical errors, which are proportional to the value of c). We can also watch this dynamic in the StateSpace1D plot as well, using a bar chart plot that looks like the figures in the main text, and should provide a great opportunity to fully observe the wave dynamics up close.

What you will see is the kinetic and potential energies moving up and down with the cur state value, while the total energy remains precisely fixed.

Thus, it seems clear that our equations are as correct as they can be, given the discretization of space and time. The only reasonable conclusion can be that the apparent energy of the global system, at least with these simple wave equations, can vary over time, but still without there being any global gain or loss over the longer time frame, which is critical for the global stability of the universe.

Feel free at this time to examine the behavior of the other variables (prv, vel, acc) in this bar-chart framework, which may help solidify the basic wave equation dynamics further.

Typically, you will now return to the [Waves Chapter](WELDBook/Waves "wikilink") and read about the 3D version of the wave equation, and then return back to the next section.

## Wave Packet in 3D

We begin our exploration of the 3D wave equation by first replicating the 1D wave packet example, using the full 3D equations, just so you can get oriented and transitioned properly in the software. We'll start by using the ControlPanel interface, which is a customizable edit panel that contains just the relevant bits of various other functionality distributed throughout the software. The underlying main 3D simulation code is controlled by the EmeWave object at the bottom of the left browser panel -- we'll explore it after our initial tour.

You should see the resulting wave packet in the left side of the display, which displays the current state value (it is labeled as C1A for reasons that we'll explain later). The right side of the display shows the velocity value, labeled as DC1A -- the derivative of C1A. This wave packet has a cross-section like the gaussian wave packet we explored with the 1D equations, but it is "extruded" out into the "depth" dimension of the display. The horizontal dimension is the **X axis**, and the depth dimension is the **Y axis** in the display geometry of the system (other systems may call this depth dimension the Z axis, but we use Z for the height axis, because we typically view a single or small number of these X-Y planes, and it is more natural to think in terms of X-Y coordinates there). This kind of wave is called a **plane wave** when it is identical along one dimension. Our wave is also the same in the Z (height) axis, as we'll see in a bit. First, let's get this wave moving!

You will see this wave packet split into two packets moving in opposite directions along the horizontal X axis, just like in the 1D case. Here, the 3D environment is 51 x 51 x 51 cells in size, which adds up (quickly!) to 132,651 individual cells -- roughly 132 times the number you used in the 1D model. If your computer has multiple CPU's, EmeWave will split the computation across these CPUs (using threads), to speed things up, but overall the speed should be reasonable on modern computing equipment.

Because they are plane waves, these wave packets do not exhibit the characteristic dissipation effects that we expect in 3D, due to the properties of the Laplacian (one reason to not true the pervasive use of plane waves in mathematical analyses). To see this, let's now create a truly 3D object -- the 3D wave packet.

This wave packet is different than the previous ones in two ways. First, as you can see, it is localized in the X and Y (and Z) axes. Second, it starts out with values initialized for the velocity (DC1A, on the right of the display). This will create a wave packet that moves to the left, instead of splitting equally into two opposing wave packets, as our previous wave packets have done.

The reason all our previous wave packets have split into two equal but opposite packets is that they start out with zero overall velocity. Thus, the total velocity of the waves in the system must remain zero -- this is a reflection of the **conservation of momentum** (another physical property that is conserved over time, like energy). The only way to have the net velocity be zero, while still having things move, is to have them move in opposite directions. This is a deep principle, which we'll encounter later in the context of entanglement, and the creation of a pair of photons out of the burst of pure energy released when an electron and positron collide. This release of equal photons traveling in opposite directions is essentially the same as our two wave packets -- and this is the main principle behind Positron Emission Tomography (PET) -- an important imaging technique for looking inside the brain and other structures.

In any case, because this wave packet starts out with an initial velocity, it will move almost entirely in one direction (there is a very tiny trace, due to numerical inaccuracies, that goes off in the other direction), making it easier to track its dissipation over time.

Now you can see that we're using wrap-around edges, so that the wave packet just wraps back around to the right after going off the edge to the left. This creates a treadmill-like effect, so we can see the wave packet lose its tight spatial localization over time. As we discussed in the chapter, this dissipation effect is inevitable, due to the way that the Laplacian integrates curvature from all different directions at the same time -- this mixes all the curvature together, and thus it inevitably spreads out over time, as the curvature originally concentrated in the X direction spreads out to the other directions.

You can also view this movie: [Movie: Matrix=512, initial wavelength=16](Media:wavebg_u512_wv16_movie.mp4 "wikilink"), to help you better see how the wave front becomes curved and stretched out. It is more obvious how the wrap-around edges enable a limited sized simulation to capture a much larger effective size, due to the linear superposition property.

Now we can get some more direct control over the simulation and display, by interacting directly with the EmeWave object that drives everything.

At the top, there are lots of basic parameters, including the size of the "universe" we're simulating, key units settings, including the speed of light (actually we enter the square of this -- c_sq), and lots of controls for what kinds of waves are being computed and in what way. For the present purposes, the is a useful parameter to look at -- it controls how edges are treated -- you can see that the CUBE}} and it is using for the waves (this basic form of wave is using the charge field values).

At the very bottom of the EmeWave object, are a number of different buttons -- you can see what they do by hovering the mouse over them, and looking at the very bottom-left of the overall EmeWave window, where a tool-tip will be displayed. Let's try experimenting with some of the display controls.

Now we can use more of the navigation tools within the context of a single plane display, which is often the easiest to process.

Lastly, we can explore the "value" dimension, which is the value of whatever is being graphed within a given display, i.e., the wave state values, which we write as "varphi" {{\< math \>}}\varphi{{\< /math \>}} for these simple waves. These are stored in the C1A charge variable in the simulator.

These controls give you the ability to fully examine whatever you want to.

## Gaussian Bump in 3D

Finally, we'll explore 3D waves in a spherical bound state, which look something like we expect electron waves to behave when bound in an atom.

This sets the edge mode to a spherical shape, with fixed edge values, and starts with a simple gaussian bump in the state value. You can see that it will just keep oscillating in the same consistent and highly symmetrical manner over time. The spherical bounds keep the wave perfectly trapped and nothing dissipates.

From a technical perspective, you can very clearly see here that the discrete approximation to the 3D Laplacian is very isomorphic -- the waves propagate spherically symmetrically, despite the presence of the cubic grid underlying it all.
