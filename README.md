
# HFL-AD

This repository provides the code and data to reproduce the experiments of our work **Solving Data Contamination in DDoS Detection: A Method Based on Hierarchical Federated Learning**.  
We implement and compare various robust aggregation methods, including our proposed HFL-AD.

## 📂 Project Structure

```
├── try1.ipynb        # Main training script (includes Krum, Trimmed Mean, RFA, FedAvg, FLTrust, HFL-AD)
├── test.ipynb        # Testing script (generates ROC curves and AUC values)
├── F1.ipynb          # Evaluation script (outputs Accuracy, Precision, Recall, F1-score)
├── try1_result/      # Folder to save training results (auto-generated after running try1.ipynb)
├── F1/               # Contains validation set data (already pre-processed as .pt files)
└── process_data/             # Processed CICDDoS2019 dataset (.csv files after cleaning)
```

## 📝 Dataset Preparation

- We use the **CICDDoS2019**, **CICIoT2023**, **CICIoMT2024** dataset.
- Preprocessing steps:
  - Remove columns with constant values across the dataset (e.g., columns where all values are 0).
  - Clean missing values (`NaN`), infinite values (`inf`), and other abnormal data.
- Validation data is provided in the `F1/` folder
- All files are preprocessed into `.pt` files.
- Due to github upload file size limitations, to reproduce the code, please download the dataset used for training in this paper first.
  - 百度网盘：https://pan.baidu.com/s/1grQa1Ky-bNXrbCkq0CVnFA?pwd=hhm4 提取码: hhm4
 

## 🛠️ Prerequisites

- Python >= 3.9
- Jupyter Notebook

## 🚀 Reproduction Steps

### 1️⃣ Training

> Run the following steps in `try1.ipynb` to train models with different aggregation methods.

1. Create an empty folder named `try1_result`:
2. Open `try1.ipynb` and configure local data distribution:
   - Modify `dirty_num`, `cluster1`, `cluster2`, `cluster3` to simulate different local data conditions (DN and DA).
3. Run all cells:
   - Menu → **Kernel** → **Restart & Run All**
4. After running, training results will be saved in `try1_result/`, where each aggregation method has its own subfolder.

### 2️⃣ Testing (ROC & AUC)

> Evaluate trained models and generate ROC curves & AUC values.

1. Open `test.ipynb`
2. Run all cells:
   - Menu → **Kernel** → **Restart & Run All**
3. The script will automatically:
   - Find the next untested experiment in `try1_result/`
   - Generate testing results including:
     - `result.json`: prediction metrics
     - ROC curve image (filename is the corresponding AUC value)

### 3️⃣ Final Evaluation (Accuracy, Precision, Recall, F1)

> Calculate classification metrics for each model.

1. Open `F1.ipynb`
2. Run all cells:
   - Menu → **Kernel** → **Restart & Run All**
3. The script will automatically:
   - Find the next experiment without evaluation results
   - Save metrics in `th.txt` under the corresponding subfolder in `try1_result/`

## 📊 Aggregation Methods Included

- FedAvg
- Krum
- Trimmed Mean
- RFA (Robust Federated Aggregation)
- FLTrust
- **HFL-AD (Our proposed method)**



## 📚 Citation

If you use this code, please cite our work: J. Gui, R. Ji, H. Huang, J. Hong and C. Hua, "Solving Data Contamination in DDoS Detection: A Method Based on Hierarchical Federated Learning," in IEEE Transactions on Information Forensics and Security, vol. 20, pp. 7013-7028, 2025, doi: 10.1109/TIFS.2025.3587185. 


## 🤝 Acknowledgement

- CICDDoS2019 dataset: https://www.unb.ca/cic/datasets/ddos-2019.html
- CICIoT2023 dataset: https://www.unb.ca/cic/datasets/IoT2023.html
- CICIoMT2024 dataset: https://www.unb.ca/cic/datasets/IoMT2024.html
