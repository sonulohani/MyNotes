### Understanding Quaternions

Quaternions are a number system that extends complex numbers and provides a convenient mathematical notation for representing orientations and rotations of objects in three dimensions. They are particularly useful in computer graphics, robotics, and physics for interpolating rotations (slerp) and avoiding gimbal lock.

#### A quaternion \( q \) is generally expressed as:

\[ q = w + xi + yj + zk \]

where:
- \( w \) is the real part.
- \( x, y, z \) are the imaginary parts.
- \( i, j, k \) are the fundamental quaternion units.

These units satisfy the following multiplication rules:

\[ i^2 = j^2 = k^2 = ijk = -1 \]  
\[ ij = k, \quad ji = -k \]  
\[ jk = i, \quad kj = -i \]  
\[ ki = j, \quad ik = -j \]

A quaternion can also be represented as a 4-tuple \( (w, x, y, z) \).

### Quaternion Operations

1. **Addition**:
   \[ q_1 + q_2 = (w_1 + w_2) + (x_1 + x_2)i + (y_1 + y_2)j + (z_1 + z_2)k \]

2. **Multiplication**:
   The product of two quaternions \( q_1 = w_1 + x_1i + y_1j + z_1k \) and \( q_2 = w_2 + x_2i + y_2j + z_2k \) is given by:
   \[ q_1 q_2 = (w_1 w_2 - x_1 x_2 - y_1 y_2 - z_1 z_2) + (w_1 x_2 + x_1 w_2 + y_1 z_2 - z_1 y_2)i + (w_1 y_2 + y_1 w_2 + z_1 x_2 - x_1 z_2)j + (w_1 z_2 + z_1 w_2 + x_1 y_2 - y_1 x_2)k \]

3. **Conjugate**:
   The conjugate of a quaternion \( q = w + xi + yj + zk \) is:
   \[ q^* = w - xi - yj - zk \]

4. **Norm**:
   The norm (or magnitude) of a quaternion \( q = w + xi + yj + zk \) is:
   \[ \|q\| = \sqrt{w^2 + x^2 + y^2 + z^2} \]

5. **Inverse**:
   The inverse of a quaternion \( q \) is given by:
   \[ q^{-1} = \frac{q^*}{\|q\|^2} \]

### Rotations using Quaternions

A rotation by an angle \( \theta \) around a unit vector \( \vec{u} = (u_x, u_y, u_z) \) can be represented by the quaternion:
\[ q = \cos\left(\frac{\theta}{2}\right) + \sin\left(\frac{\theta}{2}\right)(u_x i + u_y j + u_z k) \]

### Exercise Problems

1. **Basic Operations**:
   - Given two quaternions \( q_1 = 1 + 2i + 3j + 4k \) and \( q_2 = 2 + 1i + 0j + 1k \), find:
     1. \( q_1 + q_2 \)
     2. \( q_1 q_2 \)
     3. \( q_1^* \)
     4. \( \|q_1\| \)

2. **Rotation Quaternion**:
   - Calculate the quaternion representing a rotation of 90 degrees around the axis \( \vec{u} = (1, 0, 0) \).

3. **Inverse Quaternion**:
   - Find the inverse of the quaternion \( q = 1 + 2i + 3j + 4k \).

### Solutions

1. **Basic Operations**:
   - **Addition**:
     \[ q_1 + q_2 = (1 + 2) + (2 + 1)i + (3 + 0)j + (4 + 1)k = 3 + 3i + 3j + 5k \]

   - **Multiplication**:
     \[ q_1 q_2 = (1 \cdot 2 - 2 \cdot 1 - 3 \cdot 0 - 4 \cdot 1) + (1 \cdot 1 + 2 \cdot 2 + 3 \cdot 1 - 4 \cdot 0)i + (1 \cdot 0 + 3 \cdot 2 + 4 \cdot 1 - 2 \cdot 1)j + (1 \cdot 1 + 4 \cdot 2 + 2 \cdot 0 - 3 \cdot 1)k \]
     Simplifying:
     \[ q_1 q_2 = (2 - 2 - 0 - 4) + (1 + 4 + 3 - 0)i + (0 + 6 + 4 - 2)j + (1 + 8 + 0 - 3)k \]
     \[ q_1 q_2 = -4 + 8i + 8j + 6k \]

   - **Conjugate**:
     \[ q_1^* = 1 - 2i - 3j - 4k \]

   - **Norm**:
     \[ \|q_1\| = \sqrt{1^2 + 2^2 + 3^2 + 4^2} = \sqrt{1 + 4 + 9 + 16} = \sqrt{30} \]

2. **Rotation Quaternion**:
   - Rotation of 90 degrees (\( \theta = 90^\circ \) or \( \theta = \frac{\pi}{2} \)) around \( \vec{u} = (1, 0, 0) \):
     \[ q = \cos\left(\frac{90^\circ}{2}\right) + \sin\left(\frac{90^\circ}{2}\right)(1i + 0j + 0k) \]
     \[ q = \cos\left(\frac{\pi}{4}\right) + \sin\left(\frac{\pi}{4}\right)i \]
     \[ q = \frac{\sqrt{2}}{2} + \frac{\sqrt{2}}{2}i \]

3. **Inverse Quaternion**:
   - For \( q = 1 + 2i + 3j + 4k \):
     \[ \|q\|^2 = 1^2 + 2^2 + 3^2 + 4^2 = 30 \]
     \[ q^{-1} = \frac{q^*}{\|q\|^2} = \frac{1 - 2i - 3j - 4k}{30} = \frac{1}{30} - \frac{2}{30}i - \frac{3}{30}j - \frac{4}{30}k \]
     Simplifying:
     \[ q^{-1} = \frac{1}{30} - \frac{1}{15}i - \frac{1}{10}j - \frac{2}{15}k \]

