# Mealyze_ACDT-G12

Mealyze is an AI-based personalized meal advisory system that combines
food image recognition, a structured nutrition database, and context-aware recommendations
to support everyday meal decisions.

🚨Attention🚨
This demo uses LLaVA (GPU required), so we run it via Google Colab runtime instead of always-on GPU hosting.

Works instantly when Colab is running; if the runtime is stopped, the web demo may not work properly.

Please contact us before grading/checking, and we will start the Colab runtime immediately.

(If restarting changes the link, we will share the updated link right away.)



This repository contains the executable artifacts (model, code, database, UI)
that accompany the Final Report and Evidence Report submitted for this project.

📁 Repository Structure & File Descriptions

📄 README.md

This document.
Provides an overview of the project, repository structure, and links to external evidence and demos.

🧠 AI Model & Labels
food_classifier_mobilenetv2.h5

- Trained food image classification model.

- Architecture: MobileNetV2 (ImageNet-pretrained backbone).

- Scope: 31 food classes (MVP label space).

- Used during inference to predict the most likely food category from an uploaded image.

  

food_labels.json

- Label index mapping for the classifier.

- Defines the 31 supported food classes and their numeric IDs.

- Referenced by both training and inference pipelines.

  

🏗 Training & Inference Code
train_food_classifier_mobilenetv2.ipynb

- Training pipeline for the food image classifier.

- Includes: Data loading and preprocessing, Data augmentation, Model fine-tuning, Validation and checkpointing

- Training data: AI-Hub Korean Food Image Dataset (31-class subset). https://aihub.or.kr/aihubdata/data/view.do?dataSetSn=79

- Evaluation-only data (RWTS) is NOT used here to prevent data leakage.

  

serve_llava_mealyze_pipeline.ipynb

- Inference and service pipeline notebook.

- Demonstrates: Loading the trained image classifier, Running food image inference, Linking predictions to the structured Food DB, Generating nutrition summaries and recommendation signals

-Used as the backend logic for the Mealyze prototype.


🗄 Structured Food Database
meal_advisor_food_db_v1.csv

- Structured Food Database (300 foods).

- Used as a retrieval-based knowledge base, not for model training.

- Contains: Nutrition values (kcal, protein, fat, carbs per 1 serving), Context-aware tags (e.g., soul_food, hangover_friendly), Goal-based tags (cut_friendly, bulk_friendly, etc.), Safety & allergen tags (conservative labeling policy)

- Schema and labeling rules are documented in the Evidence Report (Appendix D).

  

🌐 Front-End Prototype
index.html

- Lightweight front-end prototype UI.

- Allows users to: Upload a food image, View AI recognition results, See nutrition information and guidance, Designed as a demonstration interface, not a production deployment.
  

📊 Usability Evidence
Mealyze – Quick Usefulness Survey.pdf

- Usability survey results (n = 10 participants).

- Includes: Quantitative ratings (usefulness, clarity, satisfaction), Average scores, Short qualitative feedback
  
- Summarized and referenced in the Evidence Report (Appendix U).

  

📑 Reports 

The following documents are included in this repository for final submission:

-Final_Report.pdf
Full project report describing motivation, system design, modeling choices, and results.


-Evidence_Report.pdf
Detailed appendix-style evidence document including:

Data sources and licenses

Food DB schema and labeling rules

Nutrition provenance samples

Usability evaluation evidence

All detailed data governance, licensing, and bias analysis are documented in Evidence_Report.pdf.


🔗 External Links

Google Drive :
https://drive.google.com/drive/folders/1BsEpLKr7FObXB2jqxgw2I5prwWADBKB7?usp=sharing

Demo Video (YouTube):
https://youtu.be/rxnG7ObackQ

Presentation Video (YouTube):
https://youtu.be/uA3Zm2kcd5Q

Live URL: https://romitty-kkk.github.io/Mealyze_ACDT-G12/


🔐 Data Governance Note

Training data, evaluation data, and service knowledge bases are strictly separated by purpose.

Raw AI-Hub images and RWTS images are not redistributed in this repository.

RWTS images are used only for qualitative robustness checks, never for training.

Nutrition values are provided as representative guide values, not medical advice.

Please refer to the Evidence Report for complete documentation.


📌 Disclaimer

Mealyze is a prototype developed for academic purposes.
All nutrition information is provided for reference only and should not be interpreted as medical or dietary advice.
