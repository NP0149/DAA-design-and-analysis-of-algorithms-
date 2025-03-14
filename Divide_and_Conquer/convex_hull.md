# Convex Hull

# Appoach-I

1)sort the points according to the x coordinate

2)find the hulls in the left and right sides

3)find the right most point in the left hull and left most point in the right hull and then find the upper tanget and lower tangent

4)merge the two hulls

```
#include <stdio.h>
#include <stdlib.h>

typedef struct Point {
    int x, y;
} Point;

// Swap function for sorting
void swap(Point *a, Point *b) {
    Point temp = *a;
    *a = *b;
    *b = temp;
}

// Comparator function for sorting points by x-coordinate
int compare(const void *p1, const void *p2) {
    Point *a = (Point *)p1;
    Point *b = (Point *)p2;
    return (a->x - b->x);
}

// Function to check the orientation of three points
int orientation(Point a, Point b, Point c) {
    int val = (b.y - a.y) * (c.x - b.x) - (b.x - a.x) * (c.y - b.y);
    if (val == 0) return 0;  // Collinear
    return (val > 0) ? 1 : -1;  // Clockwise or Counterclockwise
}

// Function to find upper and lower tangents and merge convex hulls
void mergeHulls(Point *hull1, int size1, Point *hull2, int size2, Point *mergedHull, int *mergedSize) {
    int i = 0, j = 0, k = 0;

    // Find the rightmost point of hull1 and leftmost point of hull2
    int rightmost = 0, leftmost = 0;
    for (int m = 1; m < size1; m++)
        if (hull1[m].x > hull1[rightmost].x)
            rightmost = m;

    for (int m = 1; m < size2; m++)
        if (hull2[m].x < hull2[leftmost].x)
            leftmost = m;

    // Find upper tangent
    int u1 = rightmost, u2 = leftmost;
    while (1) {
        int changed = 0;
        while (orientation(hull2[u2], hull1[u1], hull1[(u1 + 1) % size1]) == -1)
            u1 = (u1 + 1) % size1;
        while (orientation(hull1[u1], hull2[u2], hull2[(u2 - 1 + size2) % size2]) == 1)
            u2 = (u2 - 1 + size2) % size2;
        if (!changed) break;
    }

    // Find lower tangent
    int l1 = rightmost, l2 = leftmost;
    while (1) {
        int changed = 0;
        while (orientation(hull2[l2], hull1[l1], hull1[(l1 - 1 + size1) % size1]) == 1)
            l1 = (l1 - 1 + size1) % size1;
        while (orientation(hull1[l1], hull2[l2], hull2[(l2 + 1) % size2]) == -1)
            l2 = (l2 + 1) % size2;
        if (!changed) break;
    }

    // Merge hulls
    i = u1;
    while (1) {
        mergedHull[k++] = hull1[i];
        if (i == l1) break;
        i = (i + 1) % size1;
    }

    i = l2;
    while (1) {
        mergedHull[k++] = hull2[i];
        if (i == u2) break;
        i = (i + 1) % size2;
    }

    *mergedSize = k;
}

// Recursive function to compute Convex Hull using Divide and Conquer
void convexHull(Point *points, int n, Point *hull, int *hullSize) {
    if (n <= 3) {  // Base case: If there are 3 or fewer points, return them
        for (int i = 0; i < n; i++)
            hull[i] = points[i];
        *hullSize = n;
        return;
    }

    int mid = n / 2;
    Point leftHull[n], rightHull[n];
    int leftSize = 0, rightSize = 0;

    // Recursively compute hulls for left and right halves
    convexHull(points, mid, leftHull, &leftSize);
    convexHull(points + mid, n - mid, rightHull, &rightSize);

    // Merge the two hulls
    mergeHulls(leftHull, leftSize, rightHull, rightSize, hull, hullSize);
}

// Utility function to print the convex hull
void printHull(Point *hull, int hullSize) {
    for (int i = 0; i < hullSize; i++)
        printf("(%d, %d)\n", hull[i].x, hull[i].y);
}

int main() {
    Point points[] = {{0, 3}, {1, 1}, {2, 2}, {4, 4}, {0, 0}, {1, 2}, {3, 1}, {3, 3}};
    int n = sizeof(points) / sizeof(points[0]);

    // Sort points by x-coordinate
    qsort(points, n, sizeof(Point), compare);

    // Compute Convex Hull
    Point hull[n];
    int hullSize = 0;
    convexHull(points, n, hull, &hullSize);

    // Print Convex Hull
    printf("Convex Hull Points:\n");
    printHull(hull, hullSize);

    return 0;
}

```

# Complexities

Time:O(NlogN)

Space:O(1)

