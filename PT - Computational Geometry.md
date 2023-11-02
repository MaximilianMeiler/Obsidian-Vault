Previous lecture: [[PT - String Hashing]]

ANY time you add a double, add an EPS value (1e-9)

Points
- Comparison: compare by X primarily, then Y
- hypot(a, b) - returns sqrt(a^2 + b^2)
- Vectors - similar, but anchored at the origin
	- Angle between vectors - dot product
	- Cross products allows us to determine vector orientation

Lines
- ax + by + c = 0
	- Parallel if a = a' and b = b'

Polygons
- Vectors of points in a certain order
	- Start node occurs both at start and end
- Area (shoelace formula)
	- 1/2 times sum(x1 \* y2...xn \* y1) - sum(y1 \* x2...y2 \* x2)
- Point in polygon
	- Winding number algorithm
		- Sum up the angles between consec poly point pairs and the point
		- 0 if the point is not in P, otherwise it's a multiple of 2pi
	- Or, create a point far away and see how many times the line in-between these two points intersects the polygon
		- Even number - it's not inside
- Convex hull
	- Graham scan
		- Take bottom-then-right most point
		- Sort angles based on angle w that point and the x axis (right to left)
		- Start also with point 1 and n-1, these will always be in the hull
			- Keep adding 1 point at a time
			- If, at any point, the last 3 points form a cw angle (turns right), remove the last two points from the hull (point n-2 is not in the hull, retry n-1)
			- Done when you get back where you started