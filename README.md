# iPhone Body Movement Prediction

## Overview
This project analyzes IMU and GPS data collected from an iPhone to predict body movement using supervised machine learning. The data includes GPS coordinates, acceleration, angular velocity, and other sensor readings. The movement categories for initial training labels include "stop," "moving forward," "turn left," and "turn right."

## Steps Completed

### 1. **Data Collection**
- **Platform Used**: MATLAB Mobile and MATLAB desktop.
- **Sensors Enabled**:
  - GPS Position
  - Accelerometer
  - Gyroscope
  - Magnetic Field
  - Orientation
- **Sampling Rate**:
  - GPS: 1 Hz (1 data point per second).
  - Motion Sensors (e.g., accelerometer, gyroscope): 50 Hz.
- **Data Recording**:
  - Data was recorded during real-world movements, such as walking and stopping, using the MATLAB Mobile app.
  - Recorded data was saved locally on the iPhone in `.mat` format with filenames including timestamps for easy identification (e.g., `sensorlog_20241210_223746.mat`).

### 2. **Data Transfer**
- Raw `.mat` files were transferred manually to the project’s local folder structure on the laptop.
- Data was converted from `.mat` to `.csv` format for ease of use in Python.
- CSV files were stored in the `data-collection/` folder, organized by timestamped subfolders (e.g., `2024-12-10_22-37-46_Data/`).

### 3. **Visualizing GPS Data**
- **Tools Used**: Python and Folium library.
- **Steps Taken**:
  - GPS data was loaded and visualized as markers on an OpenStreetMap.
  - Paths were connected using polylines to represent movement.
  - Marker popups displayed additional information such as speed and altitude.
  - A color-coded map legend was added to distinguish movement labels.

### 4. **Labeling GPS Data**
- **Labeling Criteria**:
  - **Stop**: Speed ≤ 0.1 m/s.
  - **Moving Forward**: Speed > 0.1 m/s with minimal course changes.
  - **Turn Left/Turn Right**: Significant course changes with speed > 0.1 m/s.
- **Implementation**:
  - Labels were programmatically assigned to each second of GPS data based on speed and direction changes.
  - Labeled data was saved in the `data-collection/` folder as `labeled_position_data.csv` for further use.

## Next Steps
- **Integrate IMU Data**:
  - Combine IMU sensor data (e.g., accelerometer, gyroscope) with GPS data for more robust labeling and movement prediction.
- **Train Machine Learning Models**:
  - Use the labeled data to train supervised learning models.
  - Evaluate performance and fine-tune the models.
- **Real-Time Prediction**:
  - Implement real-time movement prediction capabilities on the iPhone using the trained model.

## Project Structure
```
project-repository/
├── data-collection/  # Raw and labeled data files
│   ├── 2024-12-10_22-37-46_Data/
│   │   ├── position_data.csv
│   │   ├── labeled_position_data.csv
├── notebooks/        # Jupyter notebooks for processing and analysis
│   ├── overlay_gps_map.ipynb
│   ├── label_data_with_gps.ipynb
├── model-training/   # Machine learning training scripts (to be implemented)
├── deployment/       # Real-time prediction scripts (to be implemented)
├── README.md         # Project documentation
```

## How to Run the Project
1. **Data Collection**:
   - Use the MATLAB Mobile app to collect GPS and IMU data.
   - Save the data locally on the phone and transfer it to the `data-collection/` folder.

2. **Visualize GPS Data**:
   - Open the `notebooks/overlay_gps_map.ipynb` notebook.
   - Run the code to visualize the GPS path on a map.

3. **Label Data**:
   - Open the `notebooks/label_data_with_gps.ipynb` notebook.
   - Run the code to assign labels to the GPS data.
   - Verify the labels using the visualized map.

## Acknowledgments
- **Tools**: MATLAB Mobile, Python, Folium, Pandas.
- **Inspiration**: Real-world applications of IMU and GPS data in robotics and autonomous systems.

