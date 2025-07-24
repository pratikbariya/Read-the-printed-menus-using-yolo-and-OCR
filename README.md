# 🧾 Printed Menu Reader (YOLOv11 + Tesseract OCR)

This project uses **YOLOv11** for object detection and **Tesseract OCR** to extract structured tabular data from **printed menu images**. The detected items are converted into a structured **CSV and JSON** output containing food item names and prices.

---

## 📦 Features

- Train or load a YOLOv11 model to detect:
  - Titles (menu item names)
  - Prices
  - Descriptions (optional)
- Use DBSCAN clustering to group bounding boxes into logical rows.
- Extract text from image crops using Tesseract OCR.
- Export results as:
  - CSV (`menu_extracted.csv`)
  - JSON 
- Visualize sample and result images.

---

## 🛠️ Setup

### 1. Install Dependencies

```bash
pip install ultralytics pytesseract opencv-python pandas scikit-learn
```

### 2. Mount Google Drive (Colab only)

```python
from google.colab import drive
drive.mount('/content/drive')
```

### 3. Unzip Dataset (Optional)

```python
import zipfile, os

zip_path = '/content/m.v1i.yolov11.zip'
extract_path = '/content/drive/MyDrive/dataset'
os.makedirs(extract_path, exist_ok=True)

with zipfile.ZipFile(zip_path, 'r') as zip_ref:
    zip_ref.extractall(extract_path)
```

---

## 📌 Notes

- DBSCAN is used to group text and prices on the same horizontal row.
- OCR accuracy can vary depending on lighting, resolution, and font.
- You can adjust `eps` in DBSCAN or whitelist characters in OCR for better results.

---

## 📄 License

MIT License – use and modify freely.

---

## 🙌 Acknowledgements

- [Ultralytics YOLOv11](https://github.com/ultralytics/ultralytics)
- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract)
- [Google Colab](https://colab.research.google.com)
- [Dataset](https://universe.roboflow.com/g-8elyd/m-ajsvu/browse?queryText=&pageSize=50&startingIndex=0&browseQuery=true)
