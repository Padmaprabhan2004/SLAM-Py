
# Online SLAM using Extended Kalman Filter (EKF-SLAM)

A complete **Extended Kalman Filter-based SLAM** implementation built for the **ROS2 TurtleBot** platform, featuring robust **sensor fusion**, **map estimation**, and **real-time visualization**.  
This project integrates classical SLAM concepts with practical robotics data pipelines and leverages **Claus Brenner’s visualization tools** from Universität Hannover for intuitive data inspection.
##  Features

- **Full EKF-SLAM pipeline**
  - Motion prediction from odometry and control inputs  
  - Landmark-based correction using LiDAR or range-bearing sensors  
  - Consistent covariance propagation and data association  

- **ROS2 Integration**
  - Subscribes to `/odom`, `/scan`, and `/tf` topics  
  - Publishes estimated pose and map for visualization in `rviz2`  
  - Compatible with **TurtleBot3 (Burger / Waffle Pi)** setups  

- **Visualization**
  - Adapted from *Claus Brenner’s “Learning Mobile Robotics”* MATLAB/Python toolset, and SLAM Lectures 
  - Generates diagnostic plots: trajectories, covariance ellipses, and landmark maps.
  - Supports log playback and offline analysis of recorded bag files.

- **Data Collection**
  - Used ROS2 TurtleBot sim for data collection
  - Includes sample datasets for reproducibility  
  - Scripts for converting ROS2 topics to plain `.txt` / `.csv` files for processing  

---

## 🧠 EKF-SLAM

EKF-SLAM fuses robot odometry and sensor observations to couple the robot state and landmark coordinates, to estimate:
\[
x = [x_r, y_r, \theta_r, x_1, y_1, x_2, y_2, ...]^T
\]
while maintaining the covariance matrix \( P \) to account for uncertainty.  
Prediction and correction steps alternate as the robot moves and observes landmarks.


