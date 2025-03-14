# Assignment 3

# A. Neural Volume Rendering

## 1. Differentiable Volume Rendering

### 1.3 Ray sampling

**Rays Visualization:**

![1_3_rays](./images/1_3_rays.png)

**Grid Visualization:**

![1_3_xy_grid](./images/1_3_xy_grid.png)

### 1.4 Point sampling

![1_4_sample_points](./images/1_4_sample_points.png)

### 1.5 Volume rendering

**Depth:**

![1_5_depth](./images/1_5_depth.png)

**Gif:**

![part_1](./images/part_1.gif)

## 2. Optimizing a basic implicit volume

**Visualization:**

![part_2](./images/part_2.gif)

## 3. Optimizing a Neural Radiance Field

**Visualization:**

![part_3](./images/part_3_idx100.gif)

## 4. NeRF Extras



# B. Neural Surface Rendering

## 5. Sphere Tracing

![part_5](./images/part_5.gif)

The implementation iteratively updates a set of points by applying an implicit function to compute a step size, then updating the points by moving them in given directions, and finally checking whether all steps are below a small threshold (1e-6) to decide when to stop, returning the final points and a convergence mask.

## 6. Optimizing a Neural SDF

**Input:**

![part_6_input](./images/part_6_input.gif)

**Output:**

![part_6](./images/part_6.gif)

## 7. VolSDF

Setting: alpha: 10.0 beta: 0.01

Compared to init beta: 0.05, with beta 0.01, the final model has more details and is sharper.

**Visualizatoin:**

![part_7](./images/part_7_beta0.01.gif)

**Geometry:**

![part_7_geometry](./images/part_7_geometry_beta0.01.gif)

1. How does high `beta` bias your learned SDF? What about low `beta`?

   Hight beta smooths the density transition around the surface, making the density decay more gradually with distance. This biases the SDF to prioritize broader, coarser geometric structures, as the loss gradients are less sensitive to small SDF errors.

   Low beta sharpens the density transition, forcing the density to concentrate sharply near the SDF’s zero-level set. This biases the SDF to focus on fine geometric details, but may amplify high-frequency noise if the SDF is under-optimized.

2. Would an SDF be easier to train with volume rendering and low `beta` or high `beta`? Why?

   Training is easier with **high beta**. A larger beta produces smoother density gradients, which stabilize optimization by preventing abrupt gradient changes. This allows the model to first learn a coarse geometry before refining details. Low beta introduces steep gradients that can cause instability, especially early in training when the SDF is poorly initialized.

3. Would you be more likely to learn an accurate surface with high `beta` or low `beta`? Why?

   Low beta. A small beta enforces a sharp density peak near the SDF’s zero-crossing, which tightly couples the density field to the true surface geometry. High beta produces a "blurred" density that tolerates SDF inaccuracies, leading to smoother but less precise surfaces. 

## 8. Neural Surface Extras

### 8.2 Fewer Training Views 

**100 training views (reference):**

![part_7](./images/part_7.gif)

![part_7_geometry](./images/part_7_geometry.gif)

**NeRF:**

![part_3_idx100](./images/part_3_idx100.gif)

**50 views:**

![part_7_idx50](./images/part_7_idx50.gif)

![part_7_geometry_idx50](./images/part_7_geometry_idx50.gif)

**NeRF:**

![part_3_idx50](./images/part_3_idx50.gif)

**20 views:**

![part_7_idx20](./images/part_7_idx20.gif)

![part_7_geometry_idx20](./images/part_7_geometry_idx20.gif)

**NeRF:**

![part_3_idx20](./images/part_3_idx20.gif)

**10 views:**

![part_7_idx10](./images/part_7_idx10.gif)

![part_7_geometry_idx10](./images/part_7_geometry_idx10.gif)

**NeRF:**

![part_3_idx10](./images/part_3_idx10.gif)

**5 views:**

![part_7_idx5](./images/part_7_idx5.gif)

![part_7_geometry_idx5](./images/part_7_geometry_idx5.gif)

**NeRF:**

![part_3_idx5](./images/part_3_idx5.gif)

**1 view:**

![part_7_idx1](./images/part_7_idx1.gif)

![part_7_geometry_idx1](./images/part_7_geometry_idx1.gif)

**NeRF:**

![part_3_idx1](./images/part_3_idx1.gif)

****





