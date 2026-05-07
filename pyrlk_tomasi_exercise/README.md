# Small Computer Vision Datasets: Shi-Tomasi + PyrLK

This zip contains two tiny synthetic datasets for classroom exercises.

The starter material is intentionally **skeleton-like**. Students are expected to fill in the OpenCV calls marked `TODO`, mainly:

- `cv2.goodFeaturesToTrack`
- `cv2.calcOpticalFlowPyrLK`
- `cv2.circle`
- `cv2.line`

## Notebook

Open:

```
starter_opencv.ipynb
```

This notebook keeps the surrounding Python minimal so students mainly practice the key OpenCV functionality.

## 1. `shi_tomasi_static/`

Use `corners_static.png` to test Shi-Tomasi corner detection.

Files:

- `corners_static.png`: grayscale image with squares, rectangle, diamond, triangle, line, and circle.
- `approx_corners.csv`: approximate expected strong corner locations.
- `corners_static_with_expected_points.png`: visualization of approximate expected corners.

Suggested student tasks:

- Fill in `cv2.goodFeaturesToTrack` in `starter_opencv.ipynb`.
- Tune `qualityLevel`, `minDistance`, and `maxCorners`.
- Compare detected corners against `approx_corners.csv`.
- Explain why the circle and long line produce fewer or less stable corners than the polygons.

## 2. `pyrlk_sequence/`

Use frames `frame_00.png` to `frame_07.png` to test Pyramidal Lucas-Kanade optical flow.

The moving object translates by approximately:

```text
(u, v) = (6, 4) pixels per frame
```

Files:

- `frame_00.png` ... `frame_07.png`: grayscale image sequence.
- `ground_truth_points.csv`: known moving feature locations for each frame.
- `ground_truth_plotted_00.png` ... `ground_truth_plotted_07.png`: each frame with ground-truth points plotted.
- `ground_truth_tracks_all.png`: all ground-truth point trajectories plotted together.

Suggested student tasks:

- Detect Shi-Tomasi corners in `frame_00.png`.
- Track them using `cv2.calcOpticalFlowPyrLK`.
- Compare tracked displacement against the known translation `(6, 4)` pixels/frame.
- Use the plotted ground-truth images to visually verify whether the tracked points are reasonable.

## Expected outputs

After students complete the TODOs, they can optionally save outputs such as:

- `shi_tomasi_static/student_detected_corners.png`
- `pyrlk_sequence/student_tracked_01.png` ... `student_tracked_07.png`
