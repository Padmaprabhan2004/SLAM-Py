
# Extended Kalman Filter for Online SLAM (EKF-SLAM)

A complete **Extended Kalman Filter-based SLAM** implementation built for the **ROS2 TurtleBot** platform, featuring robust **sensor fusion**, **map estimation**, and **real-time visualization**.  This folder integrates classical SLAM concepts with practical robotics data pipelines and has error-ellipse and headine cone visualization for SLAM task.
##  Features

- **Full EKF-SLAM logic at main.py**
  - Motion prediction from odometry and control inputs  
  - Landmark-based correction using LiDAR or range-bearing sensors  
  - Consistent covariance propagation and data association, visualization of error ellipses on exploration.

- **Visualization using logfile_viewer.py**
  - Adapted from *Claus Brenner’s Lego Robot SLAM using Py2, updated to Py3 for improving functionalities. 
  - Generates diagnostic plots: trajectories, covariance ellipses, and landmark maps.
  - Supports log playback and offline analysis of recorded bag files.

- **Data Collection**
  - Used ROS2 TurtleBot sim for data collection
  - Includes sample datasets for reproducibility  
  - Scripts for converting ROS2 topics to plain `.txt` / `.csv` files for processing  

---

## EKF-SLAM

EKF-SLAM fuses robot odometry and sensor observations to couple the robot state and landmark coordinates, to estimate:
\[
x = [x_r, y_r, \theta_r, x_1, y_1, x_2, y_2, ...]^T
\]
while maintaining the extended covariance matrix to account for uncertainty.  
Prediction and correction steps alternate as the robot moves and observes landmarks.

## Data Association and Shortcomings
High computational overhead.
Maps the nearest landmarks under a certiain radius and assigns the state vector [x,y] to the newly observed landmarks.
Data association has issues with min_radius, leading to new landmark formation.

## Usage
'''bash
python main.py \
python logfile_viewer.py
