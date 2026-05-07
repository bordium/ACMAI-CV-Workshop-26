# Visual-Inertial Robotics Mini Dataset

This is a small synthetic robotics dataset for teaching a simple vision pipeline:

```text
Shi-Tomasi corner detection -> PyrLK optical flow -> frame transformation
```

The dataset is intentionally simple. All important variables are known:

- Camera intrinsics `K`
- Optical/body frame rotation
- Robot body poses in the world
- Ground-truth 2D feature locations
- Ground-truth depth for each feature
- Ground-truth 3D landmark locations

## Frame conventions

Body frame:

```text
X forward, Y left, Z up
```

Optical camera frame:

```text
X right, Y down, Z forward/depth
```

The calibration file gives:

```text
R_optical_body
R_body_optical
```

## Main notebook

Open:

```text
exercise.ipynb
```

Students fill in the TODOs for:

- `cv2.goodFeaturesToTrack`
- `cv2.calcOpticalFlowPyrLK`
- `cv2.circle`
- `cv2.line`
- pixel/depth back-projection with `K^{-1}`
- optical -> body -> world transformations

## Files

### `frames/`

Raw grayscale camera frames:

```text
frame_00.png ... frame_07.png
```

### `ground_truth/`

- `measurements.csv`: per-frame pixel, depth, optical/body/world coordinates
- `landmarks_world.csv`: landmark positions in the world frame
- `body_poses_world.csv`: known robot body poses
- `gt_points_frame_00.png ... gt_points_frame_07.png`: ground-truth feature visualizations
- `gt_tracks_all.png`: ground-truth tracks across the sequence

### `calibration.json`

Contains camera intrinsics and frame rotation matrices.

## Learning goals

By the end, students should understand:

1. How Shi-Tomasi finds trackable points.
2. How PyrLK tracks sparse features across frames.
3. Why a pixel needs depth before it becomes a 3D point.
4. How to transform a point from optical frame to body frame to world frame.
