# Urban Scene Understanding for Artistic Video Stylization

A deep learning project for real-time artistic stylization of dashcam videos. It uses a semantic segmentation model, trained on the CityScape dataset, to understand urban scenes and transform them into an oil painting-like style.

## Project Structure

```
Urban-Scene-Understanding/
├── notebooks/
│   ├── inference.ipynb          # Main notebook for running video stylization
│   └── training.ipynb           # Notebook for model training and experimentation
├── sample_data/
│   ├── videos/                  # Sample video files for testing
│   │   ├── test-1.mp4
│   │   └── test-2.mp4
│   ├── images/                  # Sample images for testing
│   │   ├── test_video-1.png
│   │   ├── test_video-2.png
│   │   ├── frame0.jpg
│   │   └── ...
│   └── custom_dataset/          # Custom annotated data
│       ├── images/              # Original frames
│       └── masks/               # Custom segmentation masks
├── models/
│   ├── stylization_model_v1/    # Pre-trained model version 1
│   └── stylization_model_v2/    # Pre-trained model version 2 (latest)
├── archive/                     # Archived experimental models and data
└── README.md
```

## Key Features

- **Real-time Video Processing:** Applies semantic segmentation and artistic stylization to video streams.
- **Artistic Stylization:** Converts segmented scenes into an "oil painting" style with custom color mapping.
- **Pre-trained Models:** Includes multiple pre-trained models ready for inference.
- **Deep Learning Backbone:** Built with TensorFlow and Keras, utilizing U-Net-like architectures for segmentation.

## How It Works

The processing pipeline is straightforward:
1. A frame is captured from the input video.
2. The frame is preprocessed (denoising, brightness/contrast adjustment) and resized.
3. The preprocessed frame is passed to a pre-trained semantic segmentation model.
4. The model outputs a segmentation mask, classifying each pixel into categories like `road`, `vehicle`, `building`, etc.
5. A custom function maps these categories to a specific color palette, creating the oil painting effect.
6. The final stylized frame is displayed alongside the original.

## Technologies Used

- **TensorFlow / Keras** - Deep learning framework
- **OpenCV** - Computer vision and video processing
- **NumPy** - Numerical computations
- **Matplotlib** - Visualization and plotting
- **Jupyter Notebook** - Interactive development environment

## How to Run

### Prerequisites
Ensure you have the required Python libraries installed:
```bash
pip install tensorflow opencv-python matplotlib numpy
```

### Running the Inference
1. Clone this repository:
   ```bash
   git clone https://github.com/jayan110105/Urban-Scene-Understanding.git
   cd Urban-Scene-Understanding
   ```

2. Open the inference notebook:
   ```bash
   jupyter notebook notebooks/inference.ipynb
   ```

3. In the notebook, you can:
   - Change the `video_path` variable to point to your test video
   - Change the `img_path` variable to test on individual images
   - Run the cells to see the stylized output

### Running Training (Optional)
If you want to train your own models:
1. Prepare the CityScape dataset in the appropriate directory structure
2. Open `notebooks/training.ipynb`
3. Follow the training pipeline in the notebook

## Models

This repository contains pre-trained models in the `models/` directory:

- **`stylization_model_v1`**: First version of the stylization model
- **`stylization_model_v2`**: Latest and most refined version (recommended)

The models are trained on the CityScape dataset and optimized for urban scene understanding with artistic output.

## Sample Data

The `sample_data/` directory contains:
- **Videos**: Sample dashcam footage for testing the real-time stylization
- **Images**: Individual frames for quick testing and debugging
- **Custom Dataset**: Your own annotated data for further training or evaluation

## Notes

- The project uses legacy TensorFlow SavedModel format. For newer Keras versions, you may need to adapt the model loading code.
- Video processing works best with dashcam footage containing urban scenes similar to the CityScape dataset.
- The "oil painting" effect is achieved through custom color mapping of segmentation classes.
