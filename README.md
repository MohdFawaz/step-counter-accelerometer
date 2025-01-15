# Step Counter Using Accelerometer Data

## Problem Statement
This project implements a step counter using accelerometer data from a smartphone. The aim is to familiarize with reading sensor data, visualizing, and parsing data through a practical example. The implementation involves storing accelerometer data using MATLAB on a smartphone and processing it with Python to count steps.

## Implementation Overview

### Data Collection
Two datasets were collected using MATLAB Mobile:
1. First Dataset: 9-10 steps of fast walking (10 seconds)
2. Second Dataset: 12-13 steps including walking and jumping (15.65 seconds)

### Data Processing Steps

1. **Pre-processing**
   - Calculated magnitude from 3-axis data: `sqrt(x² + y² + z²)`
   - Applied IIR Butterworth low-pass filter
   - Sampling Frequency: 85 Hz
   - Cut-off Frequency: 3 Hz (based on step frequency < 2 steps/second)

2. **Step Detection Algorithms**

   a. Basic Static Threshold Method (First Implementation):
   - Used formula: `threshold = mean(filtered_magnitude) + k * std(filtered_magnitude)`
   - Counted steps when signal exceeded threshold
   - Worked well for consistent walking patterns

   b. Enhanced Dynamic Threshold Method (Second Implementation):
   - Implemented rolling window for local max/min calculation
   - Dynamic threshold calculation: `(max_val + min_val) / 2 + margin`
   - Added time window filtering for noise reduction
   - Better handling of varying peak intensities

### Results
- First Dataset (Regular Walking):
  - Actual Steps: 9-10
  - Both methods accurately detected 9 steps

- Second Dataset (Mixed Walking/Jumping):
  - Actual Steps: 12-13
  - Static Threshold: 6 steps (inaccurate)
  - Dynamic Threshold: 13 steps (accurate)

## Future Improvements
- Implement dynamic precision for step spacing
- Consider machine learning approaches
- Add advanced filtration methods for false step detection
- Optimize code architecture for better time and space complexity

## Technologies Used
- MATLAB & MATLAB Mobile for data collection
- Python for data processing and analysis
- Numpy and Matplotlib for calculations and visualization

## Repository Structure
```
project/
│
├── matlab/
│   └── data_collection.m    # Data collection script
│
├── python/
│   ├── stepcounter.py      # Main implementation
│
└── README.md               # Project documentation
```

## Author
Moh'd Fawaz Abdel Rahman Abu Quttain 
