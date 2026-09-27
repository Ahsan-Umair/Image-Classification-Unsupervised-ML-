# Image Compression with K-Means

An unsupervised computer-vision exercise that compresses an image by clustering its RGB pixels into a smaller color palette. Each pixel is replaced by the centroid of its assigned cluster, reducing the number of distinct colors while preserving the main visual structure.

## Workflow

- Load the source image with Pillow and interpret its three-channel pixel array as RGB.
- Reshape the image into a two-dimensional list of pixels.
- Fit K-means at several cluster counts and inspect inertia with the elbow method.
- Train a 16-color K-means model.
- Reconstruct and display the compressed image from cluster centroids.
- Save the original and compressed images and export the fitted model.
- Reload the artifact to demonstrate reusable compression.

## Notebook walkthrough

1. Open `Image-Classification-Image.jpeg`, inspect its array shape, and reshape the three-channel pixel array to one row per RGB pixel.
2. Sample 10,000 pixels with NumPy seed 42. Fit K-means for 2, 4, 8, 16, 32, and 64 colors on that sample and plot inertia to examine the color-palette tradeoff.
3. Fit the final 16-cluster model on **all** pixels with `random_state=42` and `n_init=10`. Replace each pixel with its assigned centroid, reshape to the original image dimensions, and cast back to 8-bit color.
4. Display original and reconstructed images side by side. Save both as PNG files and compare their disk sizes and reported percentage reduction.
5. Count pixels per cluster, print each palette color's RGB center, export the K-means model, then reload it and predict pixel labels to verify reuse.

The notebook assumes the input image has exactly three color channels. Its file-size comparison is between two PNG files; the number of palette colors does not by itself guarantee a smaller PNG.

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
