# AG News Category Prediction Microservice

This repository contains a microservice that classifies news articles into predefined categories using a machine learning model trained on the AG News dataset. The microservice is deployed on Google Cloud Run and leverages containerization for efficient management of dependencies and resource constraints.

## Project Overview

This project demonstrates the use of transfer learning techniques for text classification using the AWD_LSTM ULMFiT model. The model achieved an overall accuracy of 88% during validation, with strong precision, recall, and F1-scores across all categories. The service is designed to provide real-time predictions for news categorization, making it suitable for news platforms and content management systems.

## Features

- **Text Classification**: Automatically classifies news articles into one of four categories: World, Sports, Business, and Sci/Tech.
- **Scalability**: Deployed on Google Cloud Run, allowing the service to scale based on demand.
- **Containerization**: The service is containerized using Docker, ensuring consistent and isolated environments across different platforms.

## Dataset

The AG News dataset was used for training the model. It consists of 96,000 news articles categorized into four classes:

- **World**
- **Sports**
- **Business**
- **Sci/Tech**

A 10% subset of the dataset (9,600 observations) was used for training and validation to manage computational resources effectively.

## Project Structure

├── README.md # Project overview and setup instructions ├── app.py # Main application logic for the microservice ├── requirements.txt # Python dependencies required for the project ├── Dockerfile # Docker configuration for containerization ├── model.pkl # Trained model file ├── text_classification_with_transfer_learning.ipynb # Jupyter notebook for model training ├── screenshots/ # Screenshots of project setup and deployment │ ├── project_creation.png │ ├── service_logs.png │ └── bucket_creation.png └── presentations/ # Presentation files for the project └── AG_News_Deployment_Presentation.pptx


## Setup Instructions

### Prerequisites

- Python 3.7 or higher
- Docker
- Google Cloud SDK

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/agnewsclassifier.git
    cd agnewsclassifier
    ```

2. Install the required dependencies:

    ```bash
    pip install -r requirements.txt
    ```

3. Run the application locally:

    ```bash
    python app.py
    ```

### Deploying on Google Cloud Run

1. Build the Docker image:

    ```bash
    docker build -t agnews-category-prediction .
    ```

2. Deploy the container to Google Cloud Run:

    ```bash
    gcloud run deploy agnews-category-prediction --project ag-news-project-432100 --source . --region us-central1 --allow-unauthenticated --memory=1024Mi
    ```

### Accessing the Service

Once deployed, the service will be available at a URL similar to:

https://agnews-category-prediction-5kvzr252lq-uc.a.run.app/


Send a POST request with the news article text to get the predicted category.

## Challenges Faced

### Windows OS

- **Issue:** Despite successful deployment of all required files, the web application displayed a "Service Unavailable" error when accessed.
- **Resolution:** Deployment was delayed due to the inability to test and verify on Windows.

### macOS

- **Issue:** Challenges were faced during SDK installation with the Homebrew package manager.
- **Resolution:** Manual intervention was required to add Homebrew to the PATH variable. After resolving, the deployment was successful.

## References

- Zhang, X., Zhao, J., & LeCun, Y. (2015). *Character-level convolutional networks for text classification*. arXiv. https://arxiv.org/abs/1509.01626
- Howard, J., & Ruder, S. (2018). *Universal language model fine-tuning for text classification*. In Proceedings of the 56th Annual Meeting of the Association for Computational Linguistics (ACL 2018). arXiv. https://arxiv.org/abs/1801.06146
- Google Cloud. (n.d.). *Google Cloud SDK documentation*. Google Cloud. https://cloud.google.com/sdk/docs/install
- Howard, J., & Gugger, S. (2020). *Fastai: A layered API for deep learning*. arXiv. https://arxiv.org/abs/2002.04688
- Zhang, X., Zhao, J., & LeCun, Y. (2015). *AG News dataset*. Retrieved from https://raw.githubusercontent.com/mhjabreel/CharCnn_Keras/master/data/ag_news_csv/train.csv

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
