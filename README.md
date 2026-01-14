# Playlist App - Mood & Genre Prediction

A fullstack application that predicts song mood/genre from audio features and generates song suggestions using:
- **React** - Frontend UI
- **FastAPI** - Backend API
- **TensorFlow** - Machine learning model
- **Librosa** - Audio feature extraction
- **MTG-Jamendo Dataset** - Large-scale music dataset for training

## Features

- Upload audio files and extract features using Librosa
- Predict song mood and genre using TensorFlow
- Generate song suggestions based on the predicted vibe
- Modern, responsive UI
- Train models on MTG-Jamendo dataset (55,000+ tracks) or custom datasets

## Project Structure

```
playlist-app/
├── backend/          # FastAPI backend
│   ├── app/
│   │   ├── main.py
│   │   ├── models/
│   │   ├── services/
│   │   └── utils/
│   └── requirements.txt
├── frontend/         # React frontend
│   ├── src/
│   ├── public/
│   └── package.json
└── README.md
```

## Setup

### Backend

```bash
cd backend
pip install -r requirements.txt
uvicorn app.main:app --reload
```

### Frontend

```bash
cd frontend
npm install
npm start
```

## Training Your Model

The app comes with an untrained model. For better predictions, train on the **MTG-Jamendo dataset** or your own dataset.

### Using MTG-Jamendo Dataset (Recommended)

The MTG-Jamendo dataset contains over 55,000 tracks with high-quality annotations for genres, moods, and themes.

1. **Download metadata:**
   ```bash
   cd backend
   python scripts/download_jamendo.py --output_dir dataset/jamendo
   ```

2. **Download audio files** from the [MTG-Jamendo repository](https://github.com/MTG/mtg-jamendo-dataset)

3. **Train the model:**
   ```bash
   python train_model_jamendo.py \
       --metadata_file dataset/jamendo/autotagging_moodtheme.tsv \
       --audio_dir dataset/jamendo/audio \
       --epochs 50
   ```

### Using Custom Dataset

For custom datasets with directory structure (`dataset/genre/mood/audio_files`):
```bash
python backend/train_model.py --data_dir path/to/dataset
```

The trained model will be automatically loaded by the app. See `backend/TRAINING_GUIDE.md` for detailed instructions.

