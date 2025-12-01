# Confused Students EEG Analysis
This repository hosts the data and analysis for an investigation into student confusion, utilizing Electroencephalography (EEG) data collected while subjects watched educational videos. The goal of the analysis is to explore the relationship between EEG brainwave frequencies, attention/meditation levels, and a behavioral label indicating confusion.

## Repository Structure
The project is organized as follows:
```
├── data/
│   ├── videos/
│   │   ├── 0-9.m4v
│   ├── .DS_Store
│   ├── EEG_data.csv
│   └── demographic_info.csv
├── .gitattributes
├── .gitignore
├── README.md
└── confused_students_EEG.ipynb
```

## Data
The `data/` directory contains the raw and demographic information used for this analysis.
FileDescription
- `EEG_data.csv`: The primary dataset containing brainwave data (Delta, Theta, Alpha, Beta, Gamma frequencies), Attention, Meditation, Raw signal, Subject ID, Video ID, and the confusion labels (`predefinedlabel`, `userdefinedlabel`). It contains 12,811 total records.
- `demographic_info.csv`: Contains demographic details for each subject, including **Subject ID**, **age**, **ethnicity**, and **gender**. The notebook output shows 10 subjects (IDs 0-9).
- `videos/`: Contains the video files (`0-9.m4v`) corresponding to the VideoID column in `EEG_data.csv`.

## Analysis: 
`confused_students_EEG.ipynb` contains the complete data loading, cleaning, and statistical analysis performed on the dataset.

#### Initial Data Overview
The initial steps in the notebook focus on loading the data and performing basic checks.
- `SubjectID`: Identifies the participant (10 subjects, IDs 0-9).
- `VideoID`: Identifies the video stimulus shown (10 videos, IDs 0-9).
- `Attention`: NeuroSky Attention eSense meter value (0-100). 
- `Meditation`: NeuroSky Meditation eSense meter value (0-100).
- `Delta` ($\delta$): EEG power band: 0.5-2.75 Hz.
- `Theta` ($\theta$)EEG power band: 3.5-6.75 Hz.
- `Alpha1` ($\alpha_1$)EEG power band: 7.5-9.25 Hz.
- `predefinedlabel`: Categorical label (0 or 1 for non-confused/confused).
- `userdefinedlabel`: Categorical label (0 or 1 for non-confused/confused).

The notebook confirms that there is no missing data in the `eeg_df`. The data is generally balanced across subjects and videos, with the number of data points per subject ranging from 1,261 (Subjects 0, 9) to 1,314 (Subject 3), and per video ranging from 1,177 (Video 7) to 1,414 (Video 1).

#### Statistical Analysis & Modeling:
The second half of the notebook indicates the execution of descriptive statistics (mean, median, mode, variance, standard deviation, percentiles) for all numerical features. The subsequent, unexecuted cells likely contain the core analysis, which includes:
1. **Preprocessing**: Scaling features (using `MinMaxScaler` or `StandardScaler`).
2. **Hypothesis Testing**: Comparison of groups (e.g., confused vs. non-confused) using t-tests (`ttest_ind`).
3. **Machine Learning**: Training an **Support Vector Classifier (SVC)** model to predict confusion based on the EEG features. This involves splitting the data into training and testing sets, potentially using **Group Shuffle Split** to ensure robust cross-validation across subjects.
4. **Evaluation**: Assessing model performance using metrics like **accuracy score** and a **classification report**, including a **confusion matrix**.
