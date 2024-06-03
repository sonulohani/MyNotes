To calculate the direction between two vectors, you typically find the angle between them. This can be done using the dot product formula. Here is a step-by-step guide to calculate the angle between two vectors:

1. **Vectors Definition**:
   Let's define the two vectors as \(\vec{A}\) and \(\vec{B}\):
   \[
   \vec{A} = \begin{pmatrix} A_x \\ A_y \\ A_z \end{pmatrix}, \quad \vec{B} = \begin{pmatrix} B_x \\ B_y \\ B_z \end{pmatrix}
   \]

2. **Dot Product**:
   The dot product of \(\vec{A}\) and \(\vec{B}\) is calculated as:
   \[
   \vec{A} \cdot \vec{B} = A_x B_x + A_y B_y + A_z B_z
   \]

3. **Magnitudes of Vectors**:
   The magnitude (length) of \(\vec{A}\) and \(\vec{B}\) are:
   \[
   \|\vec{A}\| = \sqrt{A_x^2 + A_y^2 + A_z^2}, \quad \|\vec{B}\| = \sqrt{B_x^2 + B_y^2 + B_z^2}
   \]

4. **Cosine of the Angle**:
   Using the dot product and magnitudes, the cosine of the angle \(\theta\) between the two vectors is:
   \[
   \cos(\theta) = \frac{\vec{A} \cdot \vec{B}}{\|\vec{A}\| \|\vec{B}\|}
   \]

5. **Angle**:
   Finally, to find the angle \(\theta\), take the inverse cosine (arccos) of the cosine value:
   \[
   \theta = \arccos\left(\frac{\vec{A} \cdot \vec{B}}{\|\vec{A}\| \|\vec{B}\|}\right)
   \]

### Example Calculation
Let's say we have two vectors:
\[
\vec{A} = \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix}, \quad \vec{B} = \begin{pmatrix} 4 \\ 5 \\ 6 \end{pmatrix}
\]

1. **Calculate the dot product**:
   \[
   \vec{A} \cdot \vec{B} = 1 \cdot 4 + 2 \cdot 5 + 3 \cdot 6 = 4 + 10 + 18 = 32
   \]

2. **Calculate the magnitudes**:
   \[
   \|\vec{A}\| = \sqrt{1^2 + 2^2 + 3^2} = \sqrt{1 + 4 + 9} = \sqrt{14}
   \]
   \[
   \|\vec{B}\| = \sqrt{4^2 + 5^2 + 6^2} = \sqrt{16 + 25 + 36} = \sqrt{77}
   \]

3. **Calculate the cosine of the angle**:
   \[
   \cos(\theta) = \frac{32}{\sqrt{14} \cdot \sqrt{77}} = \frac{32}{\sqrt{1078}}
   \]

4. **Calculate the angle**:
   \[
   \theta = \arccos\left(\frac{32}{\sqrt{1078}}\right)
   \]

Use a calculator to find the value of \(\theta\):
   \[
   \theta \approx \arccos\left(0.307\right) \approx 72.54^\circ
   \]

Thus, the angle between the two vectors \(\vec{A}\) and \(\vec{B}\) is approximately \(72.54^\circ\).