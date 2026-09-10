# Image Compression with K-Means

An unsupervised computer-vision exercise that compresses an image by clustering its RGB pixels into a smaller color palette. Each pixel is replaced by the centroid of its assigned cluster, reducing the number of distinct colors while preserving the main visual structure.

## Workflow

- Load the source image with Pillow and convert it to RGB.
- Reshape the image into a two-dimensional list of pixels.
- Fit K-means at several cluster counts and inspect inertia with the elbow method.
- Train a 16-color K-means model.
- Reconstruct and display the compressed image from cluster centroids.
- Save the original and compressed images and export the fitted model.
- Reload the artifact to demonstrate reusable compression.

## Repository contents

| File | Purpose |
| --- | --- |
| `Image-Comprehension.ipynb` | Complete image clustering and reconstruction workflow |
| `Image-Classification-Image.jpeg` | Source image |
| `original_saved.png` | Saved original-image output |
| `compressed_saved.png` | Saved 16-color compressed output |
| `kmeans_image_compression_k16.pkl` | Exported K-means model |

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install jupyter numpy matplotlib pillow scikit-learn joblib
jupyter lab Image-Comprehension.ipynb
```

Fitting uses one sample per pixel, so larger images require more memory and compute. The saved model is tied to RGB input and a 16-color palette.
