<a href="https://taehun-ryu.github.io/projects/multi-camera-based-slam-system-development/" target="_blank" style="margin: 2px;"><img alt="Project Website" src="https://img.shields.io/badge/%F0%9F%8C%90%20Project%20Website-Personal%20Project%20Page-ffc107?color=42a5f5&logoColor=white" style="display: inline-block; vertical-align: middle;"/></a>

# ORB-SLAM3 with ANMS (Adaptive Non-Maximal Suppression)

## Project Goal
Apply SSC-based ANMS to the ORB keypoint selection stage in the ORB-SLAM3 pipeline to improve tracking stability and map point distribution.

## Quick Start
For build and run instructions, refer to [original README](README-origin.md).

## What Changed from ORB-SLAM3
### Main Change: ANMS with SSC
ANMS (Adaptive Non-Maximal Suppression) selects **strong keypoints while keeping them spatially well distributed** over the image.
Unlike plain NMS, which can leave many points clustered in textured regions, ANMS considers both response strength and suppression radius (distance to stronger neighbors) to improve coverage.

SSC (Suppression via Square Covering) is an efficient way to run ANMS **close to real-time**. It approximates circular suppression using grid-based square covering and performs a binary search on the suppression range `w` (square side `2w`) to retrieve approximately the target number of keypoints with a more uniform spatial distribution. For more details, please refer to the [original paper](https://www.researchgate.net/publication/323388062_Efficient_adaptive_non-maximal_suppression_algorithms_for_homogeneous_spatial_keypoint_distribution).

> Oleksandr Bailo, Francois Rameau, Kyungdon Joo, Jinsun Park, Oleksandr Bogdan, and In So Kweon. "Efficient adaptive non-maximal suppression algorithms for homogeneous spatial keypoint distribution." *Pattern Recognition Letters*. 2018.

### Side Changes
- **Build Settings**: Updated C++ standard from `std=c++11` to `std=c++14` for Ubuntu 22.04 compatibility.
- **ROS**: Removed ROS1 driver-related content.

## Detailed Report
For a detailed project report, see the [project page](https://taehun-ryu.github.io/projects/multi-camera-based-slam-system-development/).

## Acknowledgements
Special thanks to the great work of the following open-source contributors and projects.
- [ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3)
- [ANMS](https://github.com/BAILOOL/ANMS-Codes)
- [orb-slam3_ubuntu22.md](https://gist.github.com/bharath5673/4295e666cbe654a83226a2549a972c4f)
