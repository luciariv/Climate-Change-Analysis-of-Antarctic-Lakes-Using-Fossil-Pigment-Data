# Climate-Change-Analysis-of-Antarctic-Lakes-Using-Fossil-Pigment-Data
Master Thesis
markdown
Copiar código
# Climate Change Analysis of Antarctic Lakes Using Fossil Pigment Data

This project analyzes fossil pigment data from lake sediment cores to infer past environmental changes. The analysis includes data normalization, Principal Component Analysis (PCA), and visualization of pigment concentration profiles.

## Repository Structure

Climate_Antarctic_Lakes_Analysis/
│
├── data/
│ └── example_data.csv
│
├── scripts/
│ └── climate_antarctic_lakes_analysis.py
│
├── README.md
└── requirements.txt

markdown
Copiar código

## Getting Started

### Prerequisites

- Python 3.x
- pandas
- matplotlib
- scikit-learn

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/your-username/Climate_Antarctic_Lakes_Analysis.git
   cd Climate_Antarctic_Lakes_Analysis
Install the required Python packages:
sh
Copiar código
pip install -r requirements.txt
Running the Analysis
Navigate to the scripts directory:

sh
Copiar código
cd scripts
Run the analysis script:

sh
Copiar código
python climate_antarctic_lakes_analysis.py
Project Explanation
Data
data/example_data.csv: Contains example fossil pigment data.

csv
Copiar código
Depth,Chlorophyll_a,Carotenoids,Radiocarbon_age
0,10,5,100
2,12,6,200
4,14,7,300
6,18,9,400
8,22,12,500
10,28,15,600
12,30,16,700
14,35,18,800
16,38,20,900
18,40,22,1000
20,42,23,1100
22,45,24,1200
24,48,26,1300
26,50,27,1400
28,52,28,1500
30,55,30,1600
Scripts
scripts/climate_antarctic_lakes_analysis.py: Python script for data analysis and visualization. It performs the following tasks:

Loads the data from example_data.csv.
Normalizes the pigment concentrations.
Performs Principal Component Analysis (PCA) on the normalized data.
Plots stratigraphic profiles of the normalized pigment concentrations.
Creates a PCA biplot to visualize the results.
python
Copiar código
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.decomposition import PCA

# Load the data
data_file = '../data/example_data.csv'
df = pd.read_csv(data_file)

# Normalize pigment concentrations
df['Chlorophyll_a_norm'] = df['Chlorophyll_a'] / df['Chlorophyll_a'].max()
df['Carotenoids_norm'] = df['Carotenoids'] / df['Carotenoids'].max()

# Prepare data for PCA
pigments = df[['Chlorophyll_a_norm', 'Carotenoids_norm']]

# Perform PCA
pca = PCA(n_components=2)
pca_results = pca.fit_transform(pigments)

# Create a DataFrame for PCA results
pca_df = pd.DataFrame(data=pca_results, columns=['PC1', 'PC2'])
pca_df['Depth'] = df['Depth']

# Plot stratigraphic profiles
fig, axes = plt.subplots(nrows=1, ncols=2, figsize=(12, 6))

axes[0].plot(df['Chlorophyll_a_norm'], df['Depth'], label='Chlorophyll_a')
axes[0].invert_yaxis()
axes[0].set_xlabel('Normalized Concentration')
axes[0].set_ylabel('Depth (cm)')
axes[0].set_title('Chlorophyll_a Profile')
axes[0].legend()

axes[1].plot(df['Carotenoids_norm'], df['Depth'], label='Carotenoids', color='orange')
axes[1].invert_yaxis()
axes[1].set_xlabel('Normalized Concentration')
axes[1].set_title('Carotenoids Profile')
axes[1].legend()

plt.tight_layout()
plt.show()

# Plot PCA biplot
plt.figure(figsize=(8, 6))
scatter = plt.scatter(pca_df['PC1'], pca_df['PC2'], c=df['Depth'], cmap='viridis')
plt.colorbar(scatter, label='Depth (cm)')
plt.xlabel('Principal Component 1')
plt.ylabel('Principal Component 2')
plt.title('PCA of Pigment Data')
plt.show()
Results
The script will generate the following plots:

Stratigraphic Profiles:

Normalized concentration of Chlorophyll-a against depth.
Normalized concentration of Carotenoids against depth.
PCA Biplot:

Principal Component Analysis (PCA) results of the pigment data, with depth color-coded.
License
This project is licensed under the MIT License.

bash
Copiar código

### Steps to Complete the Repository

1. **Create the Directory Structure:**
   ```sh
   mkdir Climate_Antarctic_Lakes_Analysis
   cd Climate_Antarctic_Lakes_Analysis
   mkdir data scripts
Create example_data.csv in data/:

sh
Copiar código
cd data
nano example_data.csv
Paste the CSV content provided above.

Create climate_antarctic_lakes_analysis.py in scripts/:

sh
Copiar código
cd ../scripts
nano climate_antarctic_lakes_analysis.py
Paste the Python script content provided above.

Create requirements.txt in the root directory:

sh
Copiar código
cd ..
nano requirements.txt
Add the following content to requirements.txt:

txt
Copiar código
pandas
matplotlib
scikit-learn
Create README.md in the root directory:

sh
Copiar código
nano README.md
Paste the README content provided above.
