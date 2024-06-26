# Enhancing IR-based Fault Localization using Large Language Models

## Structure

- **chrono/**: Contains the dataset sorted by chronological order, ideal for time-based analysis.
- **dataset/**: The original dataset from Bench4BL, optimized for our specific analyses.
- **query/**: Scripts or tools used to query the dataset.
- **results/**: Outputs or results generated from the analyses.
- **LtR/**: Learning to rank framework, including training data and testing data.
	- **SimScores/**: Text similarity score.
	- **CGScores/**: Call graph score.
	- **ClassScores/**: Class name match score.