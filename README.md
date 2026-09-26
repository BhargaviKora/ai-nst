Here is a complete, polished **`README.md`** tailored for your project repository (`BhargaviKora/ai-nst`). It includes the architecture details, setup instructions, and cross-platform fixes you applied.

***

```markdown
# Real-Time Arbitrary Neural Style Transfer (AI-NST)

A full-stack deep learning web application that performs **Real-Time Arbitrary Neural Style Transfer** using PyTorch, Flask, and Bootstrap. Built upon Adaptive Instance Normalization (AdaIN), this project transfers artistic style from any style image onto a target content image in real time without requiring retraining for new image pairs.

---

##  Key Features

- **Zero-Shot Style Transfer**: Performs instant style transfer across arbitrary, unseen image pairs using Adaptive Instance Normalization (AdaIN).
- **Dynamic Style Weighting (\\(\alpha\\)-Interpolation)**: Configurable slider parameter (\\(\alpha \in [0.0, 1.0]\\)) allows users to dynamically balance content preservation versus style intensity during inference.
- **Interactive Web Interface**: Clean, responsive frontend developed with Flask, Flask-WTF, and Bootstrap 3 for seamless file uploading and image rendering.
- **Cross-Platform Compatibility**: Uses OS-agnostic path handling (`os.path.join`), running smoothly across Windows, Linux, and macOS environments.
- **Hardware Acceleration & Fallback**: Automatically leverages CUDA-enabled GPU hardware when available, with transparent fallback to CPU execution.
- **Production-Ready Configuration**: Includes WSGI Gunicorn setup (`Procfile`) ready for cloud deployment.

---

##  Model Architecture & Mechanics

1. **VGG-19 Encoder**: Features are extracted using a normalized, pre-trained VGG-19 network up to the `relu4_1` layer.
2. **Adaptive Instance Normalization (AdaIN)**: Aligns the feature channel mean and standard deviation of content representations to match those of the style input in feature space.
3. **Decoder Network**: Learns to invert stylized AdaIN feature maps back into high-resolution visual images.
4. **Joint Loss Function**: Optimizes decoder output using a weighted sum of **MSE Content Loss** and **Multi-Layer Style Loss**.

---

##  Repository Structure

```text
ai-nst/
├── NST_Code/
│   ├── app.py              # Flask application & style transfer inference pipeline
│   ├── train.py            # PyTorch model training script & loss computations
│   ├── vgg_normalised.pth  # Pre-trained VGG encoder parameters
│   ├── utils/              # Model architectures (Encoder/Decoder) & AdaIN logic
│   ├── templates/          # HTML templates for web UI
│   ├── static/uploads/     # Staging directory for input & stylized images
│   └── experiment/         # Checkpoints & model weight files (`decoder_final.pth`)
├── Demo_IO_Images/         # Sample content/style pairs and generated outputs
├── code.ipynb              # Jupyter notebook with research code and experiments
├── Procfile.txt            # WSGI Gunicorn execution script for hosting
└── requirements.txt        # Python library dependencies
```

---

##  Getting Started

### Prerequisites

- **Python**: 3.8 or higher (3.8 - 3.13 supported)
- **Git**
- **CUDA GPU** *(Optional, for accelerated inference)*

### Installation & Local Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/BhargaviKora/ai-nst.git
   cd ai-nst
   ```

2. **Create and activate a virtual environment:**
   - **Windows:**
     ```bash
     python -m venv venv
     venv\Scripts\activate
     ```
   - **macOS / Linux:**
     ```bash
     python3 -m venv venv
     source venv/bin/activate
     ```

3. **Install dependencies:**
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. **Launch the web app:**
   ```bash
   cd NST_Code
   python app.py
   ```

5. **Open in Browser:**
   Navigate to `http://localhost:5000` to run the app locally.

---

##  Tech Stack

- **Deep Learning**: PyTorch, Torchvision
- **Backend & Web**: Flask, Flask-WTF, Werkzeug, Gunicorn
- **Frontend**: HTML5, Bootstrap 3
- **Image Processing & Math**: Pillow, NumPy, tqdm
```

***
