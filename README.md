PDAN8412 – Convolutional Neural Networks
This project investigates multi-class pet-breed image classification using the Oxford-IIIT Pet Dataset. It covers exploratory data analysis, image preprocessing, a custom convolutional neural network (CNN), transfer learning with MobileNetV2, and model evaluation across 37 cat and dog breeds.
Project structure
PDAN8412_CNN_POE/
├── data/
│   ├── raw/
│   │   ├── images/          # Dataset images
│   │   └── annotations/     # Dataset annotations and official split files
│   
├── models/                  # Saved model checkpoints
├── notebooks/
│   └── PDAN8412_CNN_Analysis.ipynb
├── outputs/                 # Exported evaluation outputs
├── figures/                 # Generated charts and visualisations
├── .gitignore
├── README.md
└── requirements.txt
Dataset
The project uses the Oxford-IIIT Pet Dataset, containing images from 37 cat and dog breeds.
- Official dataset page: https://www.robots.ox.ac.uk/~vgg/data/pets/
- Images archive: https://www.robots.ox.ac.uk/~vgg/data/pets/data/images.tar.gz
- Annotations archive: https://www.robots.ox.ac.uk/~vgg/data/pets/data/annotations.tar.gz
Download and extract the archives into:
- Images: data/raw/images/
- Annotations: data/raw/annotations/
The analysis uses the official trainval and test annotations. The final modelling population contains 7,349 images: 3,680 in the official trainval partition and 3,669 in the official test partition. Eleven additional local images not listed in the official splits were excluded. Exact duplicate copies were identified during data cleaning.

The dataset is not included in this repository. Download it separately from the official source and follow its licence and attribution requirements.
Environment setup
Python 3.10 is recommended to match the development environment.
1. Create and activate a virtual environment
Windows PowerShell
py -3.10 -m venv .venv
.venv\Scripts\Activate.ps1
macOS / Linux
python3.10 -m venv .venv
source .venv/bin/activate
2. Install dependencies
python -m pip install --upgrade pip
pip install -r requirements.txt
TensorFlow installation compatibility depends on the operating system, Python version, and hardware. If installation fails, consult the official guide: https://www.tensorflow.org/install
3. Launch Jupyter
Run this command from the project root:
jupyter notebook
Open notebooks/PDAN8412_CNN_Analysis.ipynb and execute the cells in order.
Analysis workflow
1. Inspect the dataset structure, image files, and annotations.
2. Explore breed counts, dimensions, aspect ratios, file formats, colour modes, image integrity, and duplicate images.
3. Convert images to a consistent RGB representation and resize them while preserving aspect ratios.
4. Use the official dataset partitions and create a stratified training/validation split from the trainval data.
5. Train and assess a custom CNN baseline.
6. Apply transfer learning with pretrained MobileNetV2.
7. Evaluate the selected model on the held-out official test partition using accuracy, precision, recall, F1-score, and a confusion matrix.
8. Compare the original transfer-learning model with a fine-tuning experiment.
Reproducibility notes
- Run notebook cells from top to bottom so that paths, datasets, models, and evaluation variables are defined in sequence.
- The notebook expects the dataset folders to match the paths described above.
- Training time and results may vary with TensorFlow version, hardware, random seeds, and GPU availability.
- Dataset files, model checkpoints, and generated outputs are excluded from version control by .gitignore.
References
1. University of Oxford, Visual Geometry Group, “The Oxford-IIIT Pet Dataset.” https://www.robots.ox.ac.uk/~vgg/data/pets/
2. O. M. Parkhi, A. Vedaldi, A. Zisserman, and C. V. Jawahar, “Cats and Dogs,” in Proc. IEEE Conference on Computer Vision and Pattern Recognition (CVPR), 2012, pp. 3498–3505. https://ora.ox.ac.uk/objects/uuid:0c63daf0-fff5-4da2-aac7-d22ed65a6a84
3. M. Sandler, A. Howard, M. Zhu, A. Zhmoginov, and L.-C. Chen, “MobileNetV2: Inverted Residuals and Linear Bottlenecks,” in Proc. IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR), 2018, pp. 4510–4520. https://openaccess.thecvf.com/content_cvpr_2018/html/Sandler_MobileNetV2_Inverted_Residuals_CVPR_2018_paper.html