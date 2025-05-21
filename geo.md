Okay, here is a comprehensive list of geometry theorems, equations, and concepts commonly used in competitive programming contests. This list covers fundamental 2D geometry and some basic 3D concepts, along with essential computational geometry techniques.

**I. Fundamental Concepts & Tools**

1.  **Coordinate Systems:**
    *   Representing points as (x, y) in 2D, (x, y, z) in 3D.
    *   Using `double` or `long double` for precision (be mindful of floating-point errors).

2.  **Distance Formula:**
    *   Distance between two points P1(x1, y1) and P2(x2, y2): `sqrt((x2-x1)^2 + (y2-y1)^2)`
    *   In 3D: `sqrt((x2-x1)^2 + (y2-y1)^2 + (z2-z1)^2)`

3.  **Vectors:**
    *   Representing a vector from P1 to P2 as (x2-x1, y2-y1).
    *   Vector Addition/Subtraction: Component-wise.
    *   Scalar Multiplication: Multiply each component by the scalar.
    *   Magnitude (Length) of vector (vx, vy): `sqrt(vx^2 + vy^2)` (same as distance from origin).
    *   Unit Vector: Vector divided by its magnitude.

4.  **Dot Product (Scalar Product):**
    *   For vectors `a = (ax, ay)` and `b = (bx, by)`: `a . b = ax*bx + ay*by`
    *   Geometric Interpretation: `a . b = |a| |b| cos(theta)`, where theta is the angle between `a` and `b`.
    *   Use Cases: Finding the angle between vectors, checking if vectors are perpendicular (`a . b == 0`).

5.  **Cross Product (Vector Product):**
    *   **2D:** For vectors `a = (ax, ay)` and `b = (bx, by)`: `a x b = ax*by - ay*bx` (This is the magnitude of the resulting 3D vector, which points along the z-axis).
    *   Geometric Interpretation (2D): `|a x b|` is the area of the parallelogram formed by `a` and `b`. `(a x b) / 2` is the signed area of the triangle with vertices (0,0), a, and b.
    *   Sign of 2D Cross Product:
        *   `a x b > 0`: `b` is counter-clockwise from `a` (or `a` -> `b` is a left turn).
        *   `a x b < 0`: `b` is clockwise from `a` (or `a` -> `b` is a right turn).
        *   `a x b == 0`: `a` and `b` are collinear.
    *   Use Cases (2D): Checking orientation of points (collinear, clockwise, counter-clockwise), calculating area of polygons, checking segment intersection.
    *   **3D:** For vectors `a = (ax, ay, az)` and `b = (bx, by, bz)`:
        `a x b = (ay*bz - az*by, az*bx - ax*bz, ax*by - ay*bx)`
    *   Geometric Interpretation (3D): `a x b` is a vector perpendicular to both `a` and `b`. `|a x b|` is the area of the parallelogram formed by `a` and `b`.
    *   Use Cases (3D): Finding normal vectors to planes, calculating area of triangles/parallelograms in 3D.

6.  **Orientation Test (using 2D Cross Product):**
    *   Given three points P, Q, R. Check the sign of the cross product of vectors PQ and PR: `(Q.x - P.x)*(R.y - P.y) - (Q.y - P.y)*(R.x - P.x)`
    *   `> 0`: P->Q->R is counter-clockwise turn.
    *   `< 0`: P->Q->R is clockwise turn.
    *   `== 0`: P, Q, R are collinear.

7.  **Angles:**
    *   Units: Degrees vs. Radians (Trigonometric functions in C++ `cmath` use radians). Conversion: `radians = degrees * PI / 180`, `degrees = radians * 180 / PI`.
    *   Angle between vectors `a` and `b`: `acos((a . b) / (|a| |b|))` (result in radians).
    *   Angle of a vector (vx, vy) with positive x-axis: `atan2(vy, vx)` (result in radians, range (-PI, PI]).

**II. Lines and Segments**

8.  **Line Equations:**
    *   Slope-intercept: `y = mx + c` (Vertical lines are problematic).
    *   Point-slope: `y - y1 = m(x - x1)`
    *   General form: `Ax + By + C = 0` (Handles all lines, (A, B) is a normal vector).
    *   Parametric form: `P(t) = P0 + t*v` (P0 is a point on the line, v is direction vector).

9.  **Slope:** `m = (y2 - y1) / (x2 - x1)` (Undefined for vertical lines).

10. **Parallel Lines:** Have the same slope (`m1 = m2`) or both are vertical. In general form, `A1/B1 = A2/B2` (if B1, B2 != 0) or `A1*B2 = A2*B1`. Direction vectors are parallel.

11. **Perpendicular Lines:** Product of slopes is -1 (`m1 * m2 = -1`) or one is horizontal and the other is vertical. In general form, `A1*A2 + B1*B2 = 0`. Direction vectors are perpendicular (dot product is 0).

12. **Midpoint of a Segment:** For P1(x1, y1) and P2(x2, y2): `((x1+x2)/2, (y1+y2)/2)`

13. **Distance from Point to Line:** For point P(xp, yp) and line Ax + By + C = 0: `|A*xp + B*yp + C| / sqrt(A^2 + B^2)`

14. **Distance from Point to Segment:** More complex. Find the projection of the point onto the line containing the segment. If the projection falls *within* the segment, the distance is the distance from the point to the line. Otherwise, the distance is the minimum of the distances from the point to the segment's endpoints.

15. **Line-Line Intersection:** Solve the system of two linear equations (general form is easiest). Special cases: parallel (no intersection or infinite intersections if same line).

16. **Segment-Segment Intersection:** Check if segments intersect. A common method uses the orientation test:
    *   Check if (P1, Q1, P2) and (P1, Q1, Q2) have different orientations AND (P2, Q2, P1) and (P2, Q2, Q1) have different orientations. This handles general cases.
    *   Handle collinear cases separately: Check if endpoints of one segment lie on the other segment.

**III. Triangles**

17. **Sum of Angles:** Angles in a triangle sum to 180 degrees (PI radians).

18. **Area Formulas:**
    *   Base and Height: `Area = 0.5 * base * height`
    *   Using Coordinates (Shoelace formula - works for any polygon): For vertices (x1, y1), (x2, y2), (x3, y3): `Area = 0.5 * |(x1*y2 + x2*y3 + x3*y1) - (y1*x2 + y2*x3 + y3*x1)|`
    *   Using Cross Product: For vertices P, Q, R: `Area = 0.5 * |(Q-P) x (R-P)|`
    *   Using Side Lengths (Heron's Formula): Given side lengths a, b, c. Calculate semi-perimeter `s = (a+b+c)/2`. `Area = sqrt(s * (s-a) * (s-b) * (s-c))`
    *   Using Sine: `Area = 0.5 * a * b * sin(C)` (where a, b are side lengths, C is the angle between them).

19. **Pythagorean Theorem:** For a right triangle with legs a, b and hypotenuse c: `a^2 + b^2 = c^2`

20. **Law of Sines:** `a / sin(A) = b / sin(B) = c / sin(C) = 2R` (R is the circumradius).

21. **Law of Cosines:** `c^2 = a^2 + b^2 - 2ab * cos(C)` (Can be rearranged to find angles).

22. **Triangle Centers:** (Less common for basic formula application, more for geometric properties)
    *   Centroid: Intersection of medians. Divides medians in 2:1 ratio. Center of mass.
    *   Orthocenter: Intersection of altitudes.
    *   Incenter: Intersection of angle bisectors. Center of inscribed circle (incircle).
    *   Circumcenter: Intersection of perpendicular bisectors. Center of circumscribed circle (circumcircle).

**IV. Polygons (General)**

23. **Sum of Interior Angles:** For an n-sided polygon: `(n-2) * 180 degrees` or `(n-2) * PI radians`.
24. **Sum of Exterior Angles:** 360 degrees (2 PI radians).
25. **Perimeter:** Sum of side lengths.
26. **Area (Shoelace Formula):** For vertices (x1, y1), ..., (xn, yn) in order: `Area = 0.5 * |(x1*y2 + x2*y3 + ... + xn*y1) - (y1*x2 + y2*x3 + ... + yn*x1)|` (Works for any simple polygon, convex or concave).
27. **Convex vs. Concave:** A polygon is convex if for any two points inside or on the boundary, the segment connecting them is entirely inside or on the boundary. Equivalently, all internal angles are less than 180 degrees, or all turns when traversing vertices are in the same direction (all left or all right).
28. **Point in Polygon Test:**
    *   For Convex Polygons: Check if the point is on the same side of all edges (using cross product or orientation test).
    *   For Any Simple Polygon (Ray Casting or Winding Number): Draw a ray from the point in any fixed direction (e.g., positive x-axis). Count intersections with polygon edges. An odd number of intersections means the point is inside (Ray Casting). Winding number counts signed angles around the point.

**V. Circles**

29. **Equation of a Circle:** Center (h, k), radius r: `(x - h)^2 + (y - k)^2 = r^2`
30. **Area:** `PI * r^2`
31. **Circumference:** `2 * PI * r`
32. **Sector Area:** Given central angle theta (in radians): `(theta / (2*PI)) * (PI * r^2) = 0.5 * r^2 * theta`
33. **Arc Length:** Given central angle theta (in radians): `(theta / (2*PI)) * (2 * PI * r) = r * theta`
34. **Chord Length:** Distance between two points on the circle. Also `2 * r * sin(theta/2)` where theta is the central angle subtended by the chord.
35. **Properties:** Tangent is perpendicular to radius at point of tangency. Angle subtended by an arc at the center is double the angle subtended at any point on the remaining part of the circle.

**VI. 3D Geometry (Basic)**

36. **Distance:** (Covered in I.2)
37. **Vectors:** (Covered in I.3, I.4, I.5)
38. **Plane Equation:** `Ax + By + Cz + D = 0`. (A, B, C) is a normal vector to the plane.
39. **Distance from Point to Plane:** For P(xp, yp, zp) and plane Ax + By + Cz + D = 0: `|A*xp + B*yp + C*zp + D| / sqrt(A^2 + B^2 + C^2)`
40. **Volume of Tetrahedron:** Given vertices P1, P2, P3, P4. Form vectors v1 = P2-P1, v2 = P3-P1, v3 = P4-P1. Volume = `(1/6) * |v1 . (v2 x v3)|` (Scalar Triple Product).

**VII. Computational Geometry Algorithms/Techniques**

41. **Line Segment Intersection Test:** (Covered in II.16, using orientation test).
42. **Point on Segment Test:** Check if the point is collinear with the segment endpoints AND its coordinates are within the bounding box of the segment.
43. **Distance from Point to Line/Segment:** (Covered in II.13, II.14).
44. **Convex Hull:** Finding the smallest convex polygon that contains a given set of points. Common algorithms: Graham Scan, Monotone Chain (Andrew's Monotone Chain).
45. **Closest Pair of Points:** Finding the two points in a set with the minimum distance between them. Divide and Conquer is a standard efficient algorithm.
46. **Sweep Line Algorithm:** A technique used for problems involving geometric objects in a plane (e.g., finding all intersections among a set of line segments).

**VIII. Important Considerations for Competitive Programming**

*   **Floating-Point Precision:** Use `double` or `long double`. Compare floating-point numbers using an epsilon value (e.g., `abs(a - b) < 1e-9`). Avoid comparing directly with `==`.
*   **Edge Cases:** Vertical/horizontal lines, collinear points, overlapping segments, points exactly on boundaries.
*   **Integer Geometry:** Some problems use only integer coordinates. This avoids floating-point issues but requires careful handling of division (e.g., using cross products instead of slopes).
*   **Code Library:** Building a robust geometry library with basic types (Point, Vector, Line, Segment) and operations (distance, dot, cross, orientation, intersection) is highly recommended.

This list provides a strong foundation. Practice implementing these concepts and solving problems to become proficient! Good luck!



---




Okay, let's delve deeper into Euclidean geometry formulas and theorems, focusing on aspects particularly useful in competitive programming. We'll expand on the previous list and add more specific results.

**I. Fundamental Concepts (Revisited for Emphasis)**

1.  **Coordinate Geometry is Key:** While pure geometric theorems exist, competitive programming often translates geometry problems into coordinate space. Formulas derived from coordinate geometry (distance, dot product, cross product, line equations) are fundamental tools.
2.  **Precision:** Always use `double` or `long double`. Use an epsilon (`eps`) for floating-point comparisons: `abs(a - b) < eps`. A common epsilon is `1e-9` or `1e-10`.

**II. Lines and Segments (More Details)**

3.  **Section Formula:** Given a segment with endpoints P1(x1, y1) and P2(x2, y2). The point P(x, y) that divides the segment P1P2 in the ratio m:n is:
    `x = (n*x1 + m*x2) / (m + n)`
    `y = (n*y1 + m*y2) / (m + n)`
    (Midpoint is a special case where m=n=1).

4.  **Parametric Form of a Line:** A line passing through point P0 and parallel to vector `v` can be represented as `P(t) = P0 + t*v`.
    *   If P0=(x0, y0) and `v`=(vx, vy), then `x(t) = x0 + t*vx`, `y(t) = y0 + t*vy`.
    *   For a segment from P1 to P2, the parameter `t` ranges from 0 to 1. `P(0) = P1`, `P(1) = P2`.

5.  **Distance from Point to Line (Derivation):** Using vectors, the distance from point P to a line passing through P0 with direction vector `v` is `| (P - P0) x v | / |v|` (using 2D cross product magnitude). This is equivalent to the `|Ax + By + C| / sqrt(A^2 + B^2)` formula if you convert the line to general form.

6.  **Point on Segment Test (Refined):** Point Q lies on segment PR if and only if:
    *   P, Q, R are collinear (cross product (Q-P) x (R-P) is 0).
    *   Q lies within the bounding box of P and R ( `min(Px, Rx) <= Qx <= max(Px, Rx)` and `min(Py, Ry) <= Qy <= max(Py, Ry)`).

7.  **Line-Line Intersection (Using Parametric Forms):** Given two lines P1 + t*v1 and P2 + s*v2, solve for t and s: `P1 + t*v1 = P2 + s*v2`. This gives a system of two linear equations in t and s.
    *   If the determinant of the system is non-zero, there's a unique intersection point.
    *   If the determinant is zero, the lines are parallel. Check if they are the same line (e.g., by checking if P2 lies on the first line).

**III. Triangles (More Details)**

8.  **Triangle Inequality:** For side lengths a, b, c: `a + b > c`, `a + c > b`, `b + c > a`. (To form a valid triangle).

9.  **Apollonius' Theorem (Median Length):** For a triangle ABC, if m_a is the median from A to the midpoint of BC, then `b^2 + c^2 = 2 * (m_a^2 + (a/2)^2)`.

10. **Angle Bisector Theorem:** An angle bisector of a triangle divides the opposite side into two segments that are proportional to the other two sides of the triangle. If AD is the angle bisector of angle A in triangle ABC (D on BC), then `BD / DC = AB / AC`.

11. **Inradius (r) and Circumradius (R):**
    *   `r = Area / s` (where s is the semi-perimeter).
    *   `R = (abc) / (4 * Area)`

12. **Euler's Theorem (in Geometry):** Distance between the circumcenter (O) and incenter (I) is `OI^2 = R * (R - 2r)`. This implies `R >= 2r` (Euler's Inequality).

13. **Special Triangles:**
    *   **Equilateral Triangle:** Side `a`. Height `h = a * sqrt(3) / 2`. Area `Area = a^2 * sqrt(3) / 4`. Inradius `r = a / (2*sqrt(3))`. Circumradius `R = a / sqrt(3)`. `R = 2r`.
    *   **Right Triangle:** Legs `a, b`, hypotenuse `c`. `a^2 + b^2 = c^2`. Area `Area = 0.5 * a * b`. Circumcenter is the midpoint of the hypotenuse, `R = c / 2`. Inradius `r = (a + b - c) / 2`.

14. **Stewart's Theorem:** Relates the length of a cevian (a line segment from a vertex to the opposite side) to the lengths of the sides of the triangle and the segments the cevian divides the opposite side into. If a cevian of length `d` from vertex A divides side `a` into segments of length `m` and `n` (where `m` is adjacent to side `c` and `n` is adjacent to side `b`), then `b^2*m + c^2*n = a * (d^2 + m*n)`. (Apollonius' Theorem is a special case where the cevian is a median, so m=n=a/2).

**IV. Quadrilaterals (More Details)**

15. **General Quadrilateral Area:** Can be calculated by dividing it into two triangles using a diagonal and summing their areas (using Shoelace or other methods).
    *   Using diagonals d1, d2 and angle theta between them: `Area = 0.5 * d1 * d2 * sin(theta)`.

16. **Parallelogram:**
    *   Opposite sides parallel and equal. Opposite angles equal. Diagonals bisect each other.
    *   Area = base * height.
    *   Area = `a * b * sin(theta)` (where a, b are adjacent sides, theta is the angle between them).
    *   Sum of squares of diagonals = sum of squares of sides: `d1^2 + d2^2 = 2*(a^2 + b^2)`.

17. **Trapezoid (Trapezium):**
    *   One pair of parallel sides (bases b1, b2). Height h is perpendicular distance between bases.
    *   Area = `0.5 * (b1 + b2) * h`.

18. **Cyclic Quadrilateral (inscribed in a circle):**
    *   Opposite angles sum to 180 degrees.
    *   **Ptolemy's Theorem:** For a cyclic quadrilateral ABCD, `AB*CD + BC*DA = AC*BD` (product of diagonals equals sum of products of opposite sides).
    *   **Brahmagupta's Formula (Area):** For a cyclic quadrilateral with sides a, b, c, d and semi-perimeter `s = (a+b+c+d)/2`, `Area = sqrt((s-a)(s-b)(s-c)(s-d))`. (Heron's formula is a special case where d=0).

**V. Polygons (More Details)**

19. **Area using Shoelace Formula (Revisited):** For vertices (x1, y1), ..., (xn, yn) in *counter-clockwise* order:
    `Area = 0.5 * ((x1*y2 + x2*y3 + ... + xn*y1) - (y1*x2 + y2*x3 + ... + yn*x1))`
    If the vertices are in clockwise order, the result will be negative; taking the absolute value gives the area. The sign tells you the orientation.

20. **Centroid of a Polygon:** For vertices (x1, y1), ..., (xn, yn):
    `Cx = (1 / (6 * Area)) * sum( (xi + xi+1) * (xi*yi+1 - xi+1*yi) )`
    `Cy = (1 / (6 * Area)) * sum( (yi + yi+1) * (xi*yi+1 - xi+1*yi) )`
    (Indices are cyclic, i.e., x_n+1 = x_1, y_n+1 = y_1. The sum term `(xi*yi+1 - xi+1*yi)` is related to the cross product term in the Shoelace formula). This formula works for any simple polygon.

21. **Regular N-gon:**
    *   Central angle = `360/n` degrees or `2*PI/n` radians.
    *   Interior angle = `(n-2)*180/n` degrees or `(n-2)*PI/n` radians.
    *   Exterior angle = `360/n` degrees or `2*PI/n` radians.
    *   Side length `s`. Apothem `a` (distance from center to midpoint of a side). Circumradius `R`. Inradius `r` (which equals the apothem `a`).
    *   `s = 2 * R * sin(PI/n)`
    *   `s = 2 * r * tan(PI/n)`
    *   `R = r / cos(PI/n)`
    *   Area = `0.5 * Perimeter * apothem = 0.5 * (n*s) * r`
    *   Area = `0.5 * n * R^2 * sin(2*PI/n)`
    *   Area = `n * r^2 * tan(PI/n)`
    *   Area = `n * s^2 / (4 * tan(PI/n))`

**VI. Circles (More Details)**

22. **Power of a Point Theorem:** For a point P and a circle:
    *   If a line through P intersects the circle at A and B, the product `PA * PB` is constant for any such line.
    *   If P is outside the circle and a tangent from P touches the circle at T, `PT^2 = PA * PB` (where PAB is a secant line).
    *   If P is inside the circle and a chord through P has endpoints A and B, `PA * PB` is constant.
    *   This constant value is `d^2 - r^2` if P is outside (d > r) and `r^2 - d^2` if P is inside (d < r), where d is the distance from P to the circle's center and r is the radius.

23. **Angle between Tangent and Chord:** The angle between a tangent and a chord through the point of contact is equal to the angle in the alternate segment.

24. **Intersection of a Line and a Circle:** Substitute the line equation (e.g., parametric form or solve for y) into the circle equation. This results in a quadratic equation for the parameter (or x/y).
    *   Two distinct real roots: two intersection points.
    *   One real root (discriminant = 0): the line is tangent.
    *   No real roots (discriminant < 0): no intersection.

25. **Intersection of Two Circles:** Subtract the equations of the two circles. This eliminates the squared terms and results in a linear equation, which is the equation of the radical axis (the line containing the intersection points, if they exist). Find the intersection of this line with one of the circles.

**VII. Transformations (Formulas)**

26. **Translation:** To translate a point (x, y) by (dx, dy): `(x', y') = (x + dx, y + dy)`.

27. **Scaling (from origin):** To scale a point (x, y) by factors (sx, sy) from the origin: `(x', y') = (x * sx, y * sy)`.

28. **Rotation (around origin):** To rotate a point (x, y) counter-clockwise by an angle theta:
    `x' = x * cos(theta) - y * sin(theta)`
    `y' = x * sin(theta) + y * cos(theta)`
    (For clockwise rotation, use -theta or swap the signs of the sin terms).

29. **Rotation (around arbitrary point P0(x0, y0)):**
    *   Translate point P(x, y) so P0 is at the origin: `P_trans = (x - x0, y - y0)`.
    *   Rotate P_trans around the origin by theta to get P'_trans.
    *   Translate P'_trans back by (x0, y0) to get P'(x', y').
    `x' = (x - x0) * cos(theta) - (y - y0) * sin(theta) + x0`
    `y' = (x - x0) * sin(theta) + (y - y0) * cos(theta) + y0`

**VIII. Advanced/Less Common but Useful**

30. **Menelaus' Theorem:** For a triangle ABC and a transversal line that intersects lines AB, BC, CA at points D, E, F respectively, then `(AD/DB) * (BE/EC) * (CF/FA) = 1`. (Lengths are directed lengths along the lines).

31. **Ceva's Theorem:** For a triangle ABC and points D, E, F on sides BC, CA, AB respectively, the lines AD, BE, CF are concurrent (intersect at a single point) if and only if `(BD/DC) * (CE/EA) * (AF/FB) = 1`. (Lengths are directed lengths along the sides).

This expanded list provides more specific formulas and theorems that appear in competitive programming geometry problems, particularly those involving calculations of lengths, areas, angles, and positions of points relative to geometric figures. Remember that understanding the underlying concepts and being able to derive or apply these formulas in coordinate geometry is crucial.



---




Okay, let's cover the formulas for common 3D geometric shapes that might appear in competitive programming problems, typically involving calculations of volume or surface area.

**Important Note for 3D in Competitive Programming:**
Complex 3D geometry (like intersections of arbitrary 3D objects, rotations in 3D space using matrices beyond simple cases) is less common than 2D geometry. Problems usually involve simpler shapes, calculating volumes, surface areas, or basic distances/positions. Precision with floating-point numbers (`double` or `long double`) is even more critical in 3D.

Here are the formulas for common 3D shapes:

**I. Sphere**

*   **Parameters:** Radius `r`
*   **Volume:** `V = (4/3) * PI * r^3`
*   **Surface Area:** `A = 4 * PI * r^2`
*   **Equation (centered at (h, k, l)):** `(x - h)^2 + (y - k)^2 + (z - l)^2 = r^2`

**II. Cylinder**

*   **Parameters:** Radius of base `r`, height `h`
*   **Base Area (Circle):** `A_base = PI * r^2`
*   **Volume:** `V = A_base * h = PI * r^2 * h`
*   **Lateral Surface Area (Curved surface):** `A_lateral = Circumference_of_base * h = 2 * PI * r * h`
*   **Total Surface Area:** `A_total = A_lateral + 2 * A_base = 2 * PI * r * h + 2 * PI * r^2 = 2 * PI * r * (h + r)`

**III. Cone**

*   **Parameters:** Radius of base `r`, height `h`, slant height `l`
*   **Relationship:** `l = sqrt(r^2 + h^2)` (by Pythagorean theorem)
*   **Base Area (Circle):** `A_base = PI * r^2`
*   **Volume:** `V = (1/3) * A_base * h = (1/3) * PI * r^2 * h`
*   **Lateral Surface Area (Curved surface):** `A_lateral = PI * r * l = PI * r * sqrt(r^2 + h^2)`
*   **Total Surface Area:** `A_total = A_lateral + A_base = PI * r * l + PI * r^2 = PI * r * (l + r)`

**IV. Pyramid**

*   **Parameters:** Area of the base `B`, height `h` (perpendicular distance from apex to base plane)
*   **Base Shape:** Can be any polygon (triangle, square, rectangle, etc.). The area `B` depends on the base shape.
*   **Volume:** `V = (1/3) * B * h`
*   **Lateral Surface Area:** Sum of the areas of the triangular faces. This depends heavily on the shape of the base and whether the pyramid is right or oblique. For a **right pyramid** with a **regular polygon base**:
    *   Lateral Area = `0.5 * Perimeter_of_Base * Slant_Height_of_Face` (where slant height is the altitude of a triangular face).
*   **Total Surface Area:** `A_total = Lateral Surface Area + B`

**V. Prism**

*   **Parameters:** Area of the base `B`, height `h` (perpendicular distance between the two bases)
*   **Base Shape:** Can be any polygon. The two bases are congruent and parallel.
*   **Volume:** `V = B * h`
*   **Lateral Surface Area:** Sum of the areas of the side faces (parallelograms or rectangles). For a **right prism**:
    *   Lateral Area = `Perimeter_of_Base * h`
*   **Total Surface Area:** `A_total = Lateral Surface Area + 2 * B`

**VI. Cuboid (Rectangular Prism)**

*   **Parameters:** Length `l`, width `w`, height `h`
*   **Base Shape:** Rectangle (Area `l*w`)
*   **Volume:** `V = l * w * h`
*   **Surface Area:** `A = 2 * (l*w + l*h + w*h)` (Sum of areas of 6 rectangular faces)
*   **Space Diagonal:** `d = sqrt(l^2 + w^2 + h^2)`

**VII. Cube**

*   **Parameters:** Side length `s`
*   **Base Shape:** Square (Area `s^2`)
*   **Volume:** `V = s^3`
*   **Surface Area:** `A = 6 * s^2` (Sum of areas of 6 square faces)
*   **Face Diagonal:** `d_face = s * sqrt(2)`
*   **Space Diagonal:** `d_space = s * sqrt(3)`

**VIII. Basic 3D Concepts (Reminder from previous lists)**

*   **Distance between points (x1, y1, z1) and (x2, y2, z2):** `sqrt((x2-x1)^2 + (y2-y1)^2 + (z2-z1)^2)`
*   **Vectors in 3D:** (vx, vy, vz)
*   **Dot Product:** `a . b = ax*bx + ay*by + az*bz`. `a . b = |a| |b| cos(theta)`.
*   **Cross Product:** `a x b = (ay*bz - az*by, az*bx - ax*bz, ax*by - ay*bx)`. `|a x b|` is the area of the parallelogram formed by a and b. `a x b` is perpendicular to both a and b.
*   **Plane Equation:** `Ax + By + Cz + D = 0`. (A, B, C) is a normal vector.
*   **Distance from Point (xp, yp, zp) to Plane Ax + By + Cz + D = 0:** `|A*xp + B*yp + C*zp + D| / sqrt(A^2 + B^2 + C^2)`
*   **Volume of Tetrahedron:** Given vertices P1, P2, P3, P4. Form vectors v1=P2-P1, v2=P3-P1, v3=P4-P1. Volume = `(1/6) * |v1 . (v2 x v3)|` (Scalar Triple Product).

These formulas should cover most of the 3D geometry calculations you're likely to encounter in standard competitive programming problems. Remember to use `PI` with sufficient precision (e.g., `acos(-1.0L)` for `long double PI`) and handle floating-point comparisons carefully.



---



Okay, let's look at formulas specifically for **frustums**. A frustum is a portion of a solid (like a cone or a pyramid) that remains after cutting off the top by a plane parallel to the base.

There are two main types of frustums you might encounter:

1.  **Frustum of a Cone**
2.  **Frustum of a Pyramid**

The formulas are derived by considering the frustum as the large original cone/pyramid minus the smaller cone/pyramid that was cut off the top.

**I. Frustum of a Cone**

Imagine a large cone with radius `R` and height `H`. A smaller cone with radius `r` and height `h` is cut off the top by a plane parallel to the base.
The frustum is the remaining part.

*   **Parameters:**
    *   `R`: Radius of the larger base
    *   `r`: Radius of the smaller base
    *   `h_f`: Height of the frustum (perpendicular distance between the bases)
    *   `l_f`: Slant height of the frustum (distance along the slanted surface)

*   **Relationships:**
    *   The original large cone height `H` and small cone height `h` are related by similarity: `r/R = h/H`.
    *   The frustum height `h_f = H - h`.
    *   The original large cone slant height `L` and small cone slant height `l` are related by similarity: `r/R = l/L`.
    *   The frustum slant height `l_f = L - l`.
    *   By Pythagorean theorem on a cross-section: `l_f^2 = h_f^2 + (R - r)^2`. So, `l_f = sqrt(h_f^2 + (R - r)^2)`.

*   **Formulas:**
    *   **Volume (V):**
        `V = (1/3) * PI * h_f * (R^2 + R*r + r^2)`
        *Derivation idea: V_frustum = V_large_cone - V_small_cone. Using H = h_f * R / (R-r) and h = h_f * r / (R-r) and substituting into the cone volume formula V = (1/3)PI*radius^2*height, then simplifying.*

    *   **Lateral Surface Area (A_lateral):** (Area of the curved surface)
        `A_lateral = PI * (R + r) * l_f`
        `A_lateral = PI * (R + r) * sqrt(h_f^2 + (R - r)^2)`
        *Derivation idea: A_lateral_frustum = A_large_cone_lateral - A_small_cone_lateral. Using L = l_f * R / (R-r) and l = l_f * r / (R-r) and substituting into the cone lateral area formula A = PI*radius*slant_height, then simplifying.*

    *   **Total Surface Area (A_total):** (Area of both bases + lateral area)
        `A_total = Area_Base_Large + Area_Base_Small + A_lateral`
        `A_total = PI * R^2 + PI * r^2 + PI * (R + r) * l_f`
        `A_total = PI * (R^2 + r^2 + (R + r) * sqrt(h_f^2 + (R - r)^2))`

**II. Frustum of a Pyramid**

Imagine a large pyramid with base area `B_1` and height `H`. A smaller pyramid with base area `B_2` and height `h` is cut off the top by a plane parallel to the base.
The frustum is the remaining part.

*   **Parameters:**
    *   `B_1`: Area of the larger base
    *   `B_2`: Area of the smaller base
    *   `h_f`: Height of the frustum (perpendicular distance between the bases)
    *   `l_f`: Slant height of a trapezoidal face (this applies to *right* pyramids with *regular* polygon bases)

*   **Relationships:**
    *   The bases are similar polygons. The ratio of corresponding linear dimensions (like side lengths, apothem) is constant, say `k`. The ratio of areas is `k^2`: `B_2 / B_1 = k^2`. So `k = sqrt(B_2 / B_1)`.
    *   The original large pyramid height `H` and small pyramid height `h` are related by similarity: `h/H = k`.
    *   The frustum height `h_f = H - h`.
    *   For a **right pyramid with regular bases**, the slant height of a trapezoidal face `l_f` can be found using the height of the frustum `h_f` and the difference in the apothems (or corresponding altitudes of the base polygons) of the two bases. Let `a_1` and `a_2` be the apothems of the large and small bases respectively. Then `l_f^2 = h_f^2 + (a_1 - a_2)^2`.

*   **Formulas:**
    *   **Volume (V):** This formula is general for *any* pyramid frustum (right or oblique, any base shape) as long as the bases are parallel.
        `V = (1/3) * h_f * (B_1 + B_2 + sqrt(B_1 * B_2))`
        *Derivation idea: Similar to the cone, V_frustum = V_large_pyramid - V_small_pyramid. Using H = h_f / (1-k) and h = h_f * k / (1-k) where k = sqrt(B_2/B_1), and substituting into V = (1/3) * BaseArea * height, then simplifying.*

    *   **Lateral Surface Area (A_lateral):** (Sum of the areas of the trapezoidal faces)
        This depends on the shape of the base and whether the pyramid is right or oblique.
        *   For a **right pyramid with regular bases**: The lateral faces are congruent trapezoids. Let `P_1` be the perimeter of the large base and `P_2` be the perimeter of the small base.
            `A_lateral = 0.5 * (P_1 + P_2) * l_f` (where `l_f` is the slant height of a trapezoidal face).
        *   For other pyramid frustums (e.g., oblique or non-regular bases), you would need to calculate the area of each trapezoidal face individually and sum them up.

    *   **Total Surface Area (A_total):**
        `A_total = Area_Base_Large + Area_Base_Small + A_lateral`
        `A_total = B_1 + B_2 + A_lateral` (where `A_lateral` is calculated based on the specific pyramid type).

These formulas cover the common frustum calculations. Remember to use `PI` with sufficient precision and handle floating-point numbers carefully in implementation.
