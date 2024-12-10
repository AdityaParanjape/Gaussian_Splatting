# Gaussian Splatting for 3D Reconstruction
This project implements Gaussian Splatting, a technique to process 3D point clouds by mapping them to a voxel grid and applying Gaussian filters for density representation.

# Features
Feature Extraction: Detects keypoints and descriptors using SIFT.
3D Reconstruction: Triangulates points from image pairs using essential matrices.
Gaussian Splatting: Maps 3D points to voxel grids and applies Gaussian smoothing.
Visualization: Exports splatted 3D point clouds and generates visualizations.

# Requirements
Python 3.8+
Required libraries: OpenCV, NumPy, Matplotlib, SciPy, Open3D, Scikit-learn

Run: 
pip install -r requirements.txt  

# Usage
Prepare Images: Place your images in a folder (e.g., input_images).

To open the notebook run:

jupyter notebook  

Open the file gaussian_splatting.ipynb in the Jupyter Notebook interface.

Run the Notebook:
Execute all cells in order.

Outputs:
Splatted Point Cloud: Saved as .ply file in the output directory.
Visualizations: Displayed inline and saved as .png files in the output directory.

# Implementation Details
Key Components
Feature Detection and Matching:
Extracts keypoints using SIFT and matches features with a ratio test.

# 3D Reconstruction:

Computes essential matrices and camera poses. Triangulates 3D points from matched image features.

Gaussian Splatting:

Maps 3D points into a voxel grid.
Applies Gaussian filtering for density representation.

Code snippet:

def process_point_cloud(points_3d):  
    grid_size = 1024  
    grid = np.zeros((grid_size, grid_size, grid_size))  
    voxel_coords = (points_3d * (grid_size - 1)).astype(int)  
    for point in voxel_coords:  
        grid[point[0], point[1], point[2]] += 1  
    return gaussian_filter(grid, sigma=1.0)  


# Results
Splatted Point Cloud: output/gaussian_splatted_point_cloud.ply

Feature Files: .npz files for each image.

Visualizations: Raw 3D points and Gaussian splatted outputs.
