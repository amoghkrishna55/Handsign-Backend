# imagePreprocessing/imagePreprocessing/README.md

# Sign Language Prediction Flask Application

This project is a Flask application that predicts sign language gestures from images using a trained machine learning model.

## Project Structure

```
imagePreprocessing
├── model-H5
│   ├── model_new.json        # Architecture of the machine learning model
│   └── model_new.weights.h5  # Weights of the trained machine learning model
├── app.py                    # Flask application for sign language prediction
├── Dockerfile                # Instructions to build a Docker image for the application
├── requirements.txt          # Python dependencies required for the application
└── README.md                 # Documentation for the project
```

## Setup Instructions

1. **Clone the repository:**
   ```
   git clone <repository-url>
   cd imagePreprocessing
   ```

2. **Install dependencies:**
   It is recommended to use a virtual environment. You can create one using:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```
   Then install the required packages:
   ```
   pip install -r requirements.txt
   ```

3. **Run the application:**
   You can start the Flask application by running:
   ```
   python app.py
   ```
   The application will be available at `http://localhost:7867`.

## Docker Instructions

To run the application using Docker, follow these steps:

1. **Build the Docker image:**
   ```
   docker build -t sign-language-predictor .
   ```

2. **Run the Docker container:**
   ```
   docker run -p 7867:7867 sign-language-predictor
   ```

The application will be accessible at `http://localhost:7867`.

## Usage

To make predictions, send a POST request to the `/predict` endpoint with an image. You can send the image either as a file upload or as a base64 encoded string.

### Example Request

Using `curl` to send a base64 image:
```
curl -X POST http://localhost:7867/predict -H "Content-Type: application/json" -d '{"image_base64": "<base64-string>"}'
```

### Health Check

You can check the health of the application by sending a GET request to the `/health` endpoint:
```
curl http://localhost:7867/health
```

## License

This project is licensed under the MIT License.