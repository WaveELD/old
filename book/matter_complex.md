i $, where $i^2 = -1$, is what keeps these two values orthogonal --- the first value $a$ is along the real axis, and the second value $b$ is along the imaginary axis. The complex conjugate, $c^\*$, is simply subtracting the imaginary part instead of adding it (i.e., it represents a reflection along the imaginary dimension). Multiplying $c c^\* $ gives the squared magnitude of the vector, which is a single real-valued scalar number. It is the (squared) length of the hypotenuse of the vector.}}

We now introduce the symbol $\phi$ (another variant of the Greek symbol "phi", like $\varphi$) to represent a complex-valued state variable:

- $ \phi = a + i b $

  
  
$ = \varphi_a + i \varphi_b $

So, $\phi$ is composed of two separate real-valued numbers, designated $a$ and $b$ (or $\varphi_a$ and $\varphi_b$, to indicate that they are scalar state variables). A complex number is really just a way of representing two separate real valued numbers, aligned along orthogonal dimensions, in an efficient and compact manner (. It is essential to appreciate that, despite the presence of the imaginary number $i$ (where $i^2 = -1$ or $i = \sqrt{-1}$), *all you ever really have is two real-valued numbers*. There is nothing "imaginary" or mysterious or spooky about the second number in a complex number: all the $i$ does is keep these two values separate from each other. In the end, we will deconstruct all of our complex numbers into their real-valued components, and write purely real-valued expressions that determine their update rules. These expressions will be more complicated than the ones using complex numbers, but they are required for actually implementing the equations on the computer, and they also provide a more explicit and obvious indication of exactly what drives each value.

Here's a few interesting facts about complex numbers:

To do algebra on them, you just have to remember to *keep the real-values sorted separately from the imaginary ones*, but otherwise treat them just like a pair of numbers:

- $ y = a + ib $
- $ z = c + id $
- $ y + z = (a + c) + i(b + d) $
- $ y z = a c + i a d + i b c - b d $

  
  
$ = (ac - bd) + i (ad + bc) $

Notice that this multiplication rule is the same as $(a + b)(c + d) = ac + ad + bc + bd$, where you just multiply everything through, except that you end up with these $i$ terms crossing over, and when you multiply $ib$ and $id$, you end up with $i^2bd$, at which point the $i^2$ disappears into a $-1$ (i.e., it crosses over from the imaginary world into the real one).

As you should expect from , adding two complex numbers is like adding two vectors, and multiplication is just like multiplying vectors. Complex numbers really are just a compact way of writing vectors!

Multiplication by $i$: If you multiply a complex number by $i$, then you basically switch the real and imaginary parts: the real moves to the imaginary position, and the imaginary becomes real:

- $ i(a + ib) = ia - b = -b + ia $

Geometrically, this is equivalent to rotating a vector by 90 degrees! If you do this four times, you'll end up back where you started (as you would expect by doing a 360).

The complex conjugate of a complex number is just that number with imaginary dimension inverted:

- $ y^\* = a - i b $

The primary use of such a thing is to find the magnitude of a complex number (i.e., the length of the vector that it represents), as:

- $ y y^\* = (a + i b)(a - i b) $

  
  
$ = a^2 - iab + iab + b^2 $

$ = a^2 + b^2 $

This should be recognizable as simply the pythagorean theorem for the squared length of the hypotenuse of a right triangle ($a^2 + b^2 = c^2$). Again, complex numbers have no mystery: they just represent a two-valued vector.
