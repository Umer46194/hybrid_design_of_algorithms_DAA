DESIGN AND ANALYSIS OF ALGORITHM
ASSIGNMENT # 4

GROUP MEMBERS:
Muneeb-ur-Rehman	    48046
Muhammad Wasif Qamar	45815
Hassan Tasdique	        45897
Umer Shahmeer Ahmad	    46194

QUESTION:
	    Consider two algorithms, Algorithm A and Algorithm B, designed to solve the same problem. Your task is to design a hybrid algorithm that combines the best aspects of both Algorithm A         and Algorithm B to achieve improved performance.
SOLUTION:
	    ·  Sorting Problem: Algorithms like Merge Sort (Algorithm A) and Insertion Sort (Algorithm B) can be combined. Merge Sort is efficient for large datasets, while Insertion Sort is effective for small, nearly sorted arrays.
        ·  Shortest Path Problem: Dijkstra’s Algorithm (Algorithm A) and A* Search (Algorithm B) can be combined for path-finding, where Dijkstra’s works well in weighted graphs, while A* is faster with heuristic information.

Algorithm A: Merge Sort

Strengths: Divide-and-conquer approach; efficient with a time complexity of O(nlog⁡n)O(n \log n)O(nlogn) for large datasets.
Weaknesses: Not ideal for smaller arrays due to recursion overhead and extra memory usage.

Algorithm B: Insertion Sort

Strengths: Simple and efficient for small, nearly sorted arrays with a time complexity of O(n2)O(n^2)O(n2).
Weaknesses: Inefficient for larger datasets; lacks divide-and-conquer capability.

The hybrid design will incorporate the best features of both algorithms by using Merge Sort's structure for large datasets but switching to Insertion Sort for smaller sub-arrays during the merge process. Here’s how it could work:
1.Divide Step: Continue to split the array as in Merge Sort.
2.Switch to Insertion Sort: Once a sub-array size falls below a threshold (e.g., 10–20 elements), switch to Insertion Sort instead of continuing with recursive calls.
3.Merge Step: After sorting small sub-arrays with Insertion Sort, merge them back using the merge process in Merge Sort.

Theoretical Analysis

Time Complexity: The hybrid algorithm retains the O(nlog⁡n)O(n \log n)O(nlogn) complexity of Merge Sort for larger datasets, but with smaller sub-arrays, it performs efficiently by reducing recursive calls.

Space Complexity: Similar to Merge Sort; however, slightly reduced due to fewer recursive calls when switching to Insertion Sort for small sub-arrays.
Experimental Analysis
To validate, we can run the hybrid algorithm on different input sizes and compare with standard Merge Sort and Insertion Sort. Key metrics include:

Execution Time: Measure time for each algorithm over multiple array sizes.

Memory Usage: Track memory usage for recursion and merging steps.


After implementing, test the hybrid algorithm against both Merge Sort and Insertion Sort over various array sizes to compare:
Small arrays: Hybrid should be slightly faster than Merge Sort due to reduced recursive calls.

Large arrays: Performance similar to Merge Sort but potentially better in practical runtime due to early Insertion Sort handling for small subarrays.

CODE:
