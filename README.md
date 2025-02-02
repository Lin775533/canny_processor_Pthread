# Gaussian Blur Parallelization in Canny Edge Detection

This project demonstrates parallel implementations of the Gaussian blur operation using OpenMP and Pthreads. Both versions optimize the horizontal (`blur_x`) and vertical (`blur_y`) blur operations in the Canny edge detection algorithm.


### Performance Results

* Initial `blur_x` parallelization achieved a 16.3% improvement in processing time
* Additional `blur_y` optimization resulted in a 10.3% performance increase
* Total execution time was reduced from 0.836s to 0.750s

## Pthread Implementation

### Overview

The Pthread version implements custom thread management for fine-grained control over parallel processing. It utilizes a structured approach for data sharing and workload distribution across threads.

### Implementation Details

```c
#define N_T 4  // Number of threads

struct thread_args {
    // Thread parameters structure
    unsigned char *image;
    int rows, cols, start, end, center;
    // Additional parameters
};
```

### Performance Results

* Initial `blur_x` parallelization showed a 15.2% improvement
* Additional `blur_y` optimization achieved an impressive 87.8% improvement
* Total execution time was reduced from 0.847s to 0.103s

## Performance Considerations

While both implementations demonstrate significant improvements in static image processing, performance characteristics may vary with real-time camera input due to several factors:

* I/O bottlenecks and memory operation overhead
* Frame synchronization requirements
* Data transfer constraints between CPU and memory
* System resource availability and concurrent processes


