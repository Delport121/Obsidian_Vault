The following are functions that can be used in open3D for downsampling.

| Method | Description | Best Use Case |
|--------|------------|--------------|
| **Voxel Downsampling** | Groups points into voxel grids | Uniform reduction of density |
| **Uniform Downsampling** | Selects every `n`-th point | Fast but may lose local details |
| **Random Downsampling** | Selects a fraction of points randomly | Quick approximation |
| **Statistical Outlier Removal** | Removes points deviating from neighbors | Noise filtering & downsampling |
| **Radius Outlier Removal** | Removes sparse points with few neighbors | Isolates dense clusters |
