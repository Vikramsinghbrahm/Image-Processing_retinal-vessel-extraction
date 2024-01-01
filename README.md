# Image-Processing_retinal-vessel-extraction

This project implements the retinal vessel extraction algorithm proposed by Zhang et al. in the paper titled "Retinal vessel extraction by matched filter with first-order derivative of Gaussian."

## Overview

The goal of this project is to extract retinal vessels from retinal images using the matched filter with the first-order derivative of the Gaussian (FDOG) technique. The implementation includes preprocessing steps, filtering with matched filters, and final processing to obtain accurate vessel extraction.

## Features

- **Image Loading and Preprocessing:** Load retinal images and preprocess them for optimal vessel extraction.

- **Matched Filter with Gauss Derivative:** Apply matched filter with the first-order derivative of the Gaussian for retinal vessel enhancement.

- **Final Processing:** Combine the results from multiple directions to obtain the final vessel extraction.

- **Evaluation Metrics:** Calculate and display metrics such as accuracy, true positive rate (TPR), false positive rate (FPR), specificity, and sensitivity.

## Requirements

- Python
- OpenCV
- NumPy
- Matplotlib
- Scikit-image
- Scikit-learn

## Usage

1. **Clone the repository:**

  ```bash
  git clone https://github.com/your-username/retinal-vessel-extraction.git
  cd retinal-vessel-extraction
  ```

2. **Install the required dependencies:**

  ```bash
  pip install -r requirements.txt
  ```

3. **Usage**

    Open the Jupyter Notebook file: retinal_vessel_extraction.ipynb.
    Follow the instructions and run the cells to execute the retinal vessel extraction process.

4. **Example**
  ```bash
  # Load the image and ground truth
  img_path = "path/to/retinal_image.tif"
  ground_path = "path/to/ground_truth.png"
  img_filtered = preprocess_image(img_path)  # Use the preprocessed image
  ground_truth = load_ground_truth(ground_path)
  
  # Apply MatchFilterWithGaussDerivative for the first set of parameters
  MF_Result1, FDOG_Result1 = get_D_H(img_filtered, s=1.5, L=9, t=3,
                                     num_of_directions=8, W_size=31, c_factor=2.3)
  result1 = final_processing(MF_Result1, FDOG_Result1, img_filtered)
  
  # Apply MatchFilterWithGaussDerivative for the second set of parameters
  MF_Result2, FDOG_Result2 = get_D_H(img_filtered, s=1, L=5, t=3,
                                     num_of_directions=8, W_size=31, c_factor=2.3)
  result2 = final_processing(MF_Result2, FDOG_Result2, img_filtered)
  
  # Perform bitwise OR operation
  final_result = cv2.bitwise_or(result1, result2)
  
  # Calculate and print accuracy, TPR, FPR, Specificity, Sensitivity
  TP, FP, TN, FN = calculate_confusion_matrix(final_result, ground_truth)
  accuracy = calculate_accuracy(final_result, ground_truth)
  tpr, fpr = calculate_tpr_fpr(final_result, ground_truth)
  specificity = calculate_specificity(TN, FP)
  sensitivity = calculate_sensitivity(TP, FN)
  
  print(f'Accuracy: {accuracy}')
  print(f"True Positive Rate (TPR): {tpr}")
  print(f"False Positive Rate (FPR): {fpr}")
  print(f"Specificity: {specificity}")
  print(f"Sensitivity: {sensitivity}")

  ```
## Results
The project provides visualizations of the intermediate steps and the final extracted retinal vessels.

## Acknowledgments
Zhang, Bob & Zhang, Lin & Zhang, Lei & Karray, Fakhri. (2010). Retinal vessel extraction by matched filter with first-order derivative of Gaussian. Computers in biology and medicine. 40. 438-45. 10.1016/j.compbiomed.2010.02.008.
