# 🌟 Machine Translation Fine-tuning with Sarvam/Gemma3 ✨

🚀 **Transform your language models with powerful fine-tuning capabilities!** This repository contains a complete pipeline for fine-tuning the Sarvam/Gemma3 model for machine translation tasks. Perfect for Indic languages and beyond! 🌍

## 📁 Project Structure 🗂️

```
├── 🔧 finetune.py      # Main fine-tuning script
├── 🔗 merge.py         # LoRA adapter merging script
├── 📊 result.py        # Model evaluation and result generation
├── ⚡ generate.py      # Translation inference script
├── 📋 requirements.txt # Python dependencies
└── 📖 README.md        # This file
```

## 🚀 Quick Start 🏁

### 1. 🛠️ Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. 📝 Prepare Your Dataset 

Create `train.json` and `valid.json` files with your translation pairs. The JSON format should be:

```json
[
  {
    "sanskrit": "जटाटवीगलज्जलप्रवाहपावितस्थले",
    "bengali": "জটাটবীগলজ্জলপ্রবাহপাবিতস্থলে"
  },
  {
    "sanskrit": "गलेऽवलम्ब्य लम्बितां भुजंगतुंगमालिकाम्",
    "bengali": "গলেঽবলম্ব্য লম্বিতাং ভুজংগতুংগমালিকাম্"
  },
  {
    "sanskrit": "श्रीगुरु चरन सरोज रज निज मनु मुकुरु सुधारि",
    "bengali": "শ্রীগুরু চরন সরোজ রজ নিজ মনু মুকুরু সুধারি"
  },
  {
    "sanskrit": "बरनउं रघुबर बिमल जसु जो दायकु फल चारि",
    "bengali": "বরনউং রঘুবর বিমল জসু জো দায়কু ফল চারি"
  }
]
```

### 3. ⚙️ Configure Language Settings 🌐

Open `finetune.py` and modify these parameters according to your language pair:

```python
# Dataset Configuration 📊
SOURCE_KEY = "sanskrit"       # Key name in JSON for source language 
TARGET_KEY = "bengali"        # Key name in JSON for target language

# Language Configuration 🗣️
SOURCE_LANGUAGE = "Sanskrit"  # Change this to your source language
TARGET_LANGUAGE = "Bengali"   # Change this to your target language
```

**🎯 Example configurations for different language pairs:**

🕉️ **For Sanskrit → Tamil:**
```python
SOURCE_KEY = "sanskrit"
TARGET_KEY = "tamil"
SOURCE_LANGUAGE = "Sanskrit"
TARGET_LANGUAGE = "Tamil"
```

## 🎯 Usage Guide 💫

### Step 1: 🔥 Fine-tune the Model

```bash
python finetune.py
```

✨ **This script will:**
- 📥 Load the Sarvam/Gemma3 base model
- 🔧 Create LoRA adapters for efficient fine-tuning
- 🎓 Train on your dataset
- 💾 Save the fine-tuned adapters

### Step 2: 🔗 Merge LoRA Adapters

```bash
python merge.py
```

🎉 This merges the LoRA adapters with the base model to create a standalone fine-tuned model.

### Step 3: 📊 Evaluate Results

```bash
python result.py
```

⚙️ Configure the same language settings in `result.py`:
```python
SOURCE_KEY = "sanskrit"       # Must match finetune.py ✅
TARGET_KEY = "bengali"        # Must match finetune.py ✅
SOURCE_LANGUAGE = "Sanskrit"  # Must match finetune.py ✅
TARGET_LANGUAGE = "Bengali"   # Must match finetune.py ✅
```

📈 This script evaluates the model performance on your validation set and generates translation quality metrics.

### Step 4: ⚡ Generate Translations

```bash
python generate.py
```

🎛️ **The generation script supports two modes:**

#### 💬 Single Sentence Translation
```python
USE_FILE_MODE = False        # Set to False for single sentence 🔄
USE_SENTENCE_MODE = True     # Set to True for single sentence translation ✅
```

#### 📄 File Translation
```python
USE_FILE_MODE = True         # Set to True for file translation 📁
USE_SENTENCE_MODE = False    # Set to False when using file mode ❌
```

📂 For file translation, place your input text file in the project directory and specify the filename in the script.

## ⚙️ Configuration Parameters 🎛️

### 🔑 Key Parameters to Modify

1. **🌐 Language Configuration** (in `finetune.py`, `result.py`):
   ```python
   SOURCE_KEY = "your_source_key"
   TARGET_KEY = "your_target_key"
   SOURCE_LANGUAGE = "Your Source Language"
   TARGET_LANGUAGE = "Your Target Language"
   ```

2. **📚 Dataset Files**:
   - `train.json`: Training data with source-target pairs 🎓
   - `valid.json`: Validation data with source-target pairs ✅

3. **🎯 Translation Mode** (in `generate.py`):
   ```python
   USE_FILE_MODE = True/False     # File vs sentence mode 📁💬
   USE_SENTENCE_MODE = True/False # Single sentence translation ⚡
   ```

## 📊 Dataset Format 📋

Your JSON files should contain translation pairs with consistent keys:

```json
[
  {
    "source_language_key": "source text",
    "target_language_key": "target text"
  }
]
```

## 🔍 Example Workflows 🎯

### 🕉️ Sanskrit → Bengali Translation
1. 🔧 Set `SOURCE_KEY = "sanskrit"`, `TARGET_KEY = "bengali"`
2. 🌐 Set `SOURCE_LANGUAGE = "Sanskrit"`, `TARGET_LANGUAGE = "Bengali"`
3. 📝 Create datasets with Sanskrit-Bengali pairs
4. 🚀 Run the complete pipeline

### 🇮🇳 Hindi → Tamil Translation
1. 🔧 Set `SOURCE_KEY = "hindi"`, `TARGET_KEY = "tamil"`
2. 🌐 Set `SOURCE_LANGUAGE = "Hindi"`, `TARGET_LANGUAGE = "Tamil"`
3. 📝 Create datasets with Hindi-Tamil pairs
4. 🚀 Run the complete pipeline

## 💡 Pro Tips & Notes 📝

- ✅ Ensure consistent language key naming across all scripts
- 🌍 The model supports various Indic language pairs
- 🖥️ Adjust batch size and learning rate in `finetune.py` based on your hardware
- 📈 Monitor training progress and validation loss during fine-tuning
- 🎯 Use quality parallel data for better translation results
- 🔥 Start with smaller datasets to test your configuration

## 🎨 Features & Highlights ✨

- 🚀 **Fast & Efficient**: LoRA-based fine-tuning for quick adaptation
- 🌍 **Multi-language Support**: Perfect for Indic languages
- 📊 **Comprehensive Evaluation**: Built-in metrics and result analysis
- ⚡ **Flexible Inference**: Both file and sentence-level translation
- 🎯 **Easy Configuration**: Simple parameter adjustment
- 📚 **Rich Examples**: Sanskrit verses and devotional texts included

## 🤝 Contributing 💪

🎉 Feel free to submit issues and enhancement requests! We love community contributions! 

## 📄 License 📜

This project is licensed under the MIT License. 🆓

---

⭐ **Don't forget to star this repository if it helps you!** ⭐

🙏 **Happy Fine-tuning!** 🚀✨
