# EcoShop: Project Setup & Developer Guide

## Overview

EcoShop is a web-based sustainable e-commerce platform that promotes eco-friendly products, community-driven initiatives, and the principles of the Circular Economy. The platform allows users to register, log in, buy and sell eco-friendly products, and engage in sustainability-focused community events. It also integrates AI-driven recycling ideas, hybrid product recommendations, and deep learning image classification to categorize products accurately.

## Features

- **User Authentication**: Registration, login, and logout functionalities with secure password handling (`Flask-Bcrypt`).
- **Product Management**: Users can upload, edit, and delete eco-friendly products. Products include categories such as `"organic"` and `"recycle"`.
- **AI Chat**: Users can get AI-generated recycling and upcycling ideas based on their inputs (`Qwen/Qwen2.5-0.5B` + LangChain).
- **Community Engagement**: Users can post and manage sustainability-focused community events with pagination and multi-image uploads.
- **Image Classification**: Uses a pre-trained Convolutional Neural Network (`model_small.h5`) to classify and categorize uploaded product images automatically.
- **Hybrid Recommendation Engine**: Suggests similar eco-friendly products combining TF-IDF text vectorization and MinMax-scaled numerical attributes (`price`, `weight`, `quantity`).
- **MongoDB Database**: All data is stored in MongoDB, including user accounts, products, community posts, and purchases.

## Technologies Used

- **Backend**: Python, Flask
- **Database**: MongoDB (`pymongo`)
- **Image Processing & Classification**: PIL (Pillow), TensorFlow, Keras, NumPy
- **Generative AI & NLP**: Hugging Face `transformers` (`Qwen/Qwen2.5-0.5B`), `langchain`
- **Recommendation System**: `scikit-learn` (`TfidfVectorizer`, `cosine_similarity`, `MinMaxScaler`), `pandas`
- **Security**: `Flask-Bcrypt` for password hashing
- **Web Templates**: Jinja2 for rendering dynamic HTML pages
- **Frontend**: HTML5, CSS3, Bootstrap

## Requirements

To run this project locally, you need the following installed:

- Python 3.x
- MongoDB (running locally on `mongodb://localhost:27017`)
- Dependencies listed in `requirements.txt`:
  - `Flask`
  - `flask-bcrypt`
  - `pymongo`
  - `tensorflow`
  - `keras`
  - `Pillow`
  - `numpy`
  - `pandas`
  - `scikit-learn`
  - `transformers`
  - `langchain`

You can install the dependencies using `pip`:

```bash
pip install -r requirements.txt
pip install pandas scikit-learn keras
```

## Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/harichselvamc/EcoShop.git
   cd EcoShop
   ```

2. **Start MongoDB**:
   Ensure you have MongoDB installed and running on your local machine at `mongodb://localhost:27017`. If you haven't installed MongoDB, follow the [MongoDB installation guide](https://docs.mongodb.com/manual/installation/).

3. **Run the Flask Application**:
   Start the Flask app by running:
   ```bash
   python app.py
   ```
   Or on Windows, double-click / run `run.bat`:
   ```cmd
   run.bat
   ```
   The app will be hosted at `http://127.0.0.1:5000/` in your browser.

4. **Upload Product Images**:
   When uploading products, ensure that you follow the supported image formats (`.jpg`, `.jpeg`, `.png`, or `.gif`).

## Features in Detail

### 1. **Home Page (`/`)**:
   - Displays featured products along with their details (name, price, description, category, owner, etc.).
   - Users can navigate to product listings, community posts, recommendations, or the AI chat assistant.

### 2. **User Registration & Login (`/register`, `/login`, `/logout`)**:
   - Secure authentication with password hashing (`Flask-Bcrypt`).
   - Users can register, log in, and manage their own product listings and community events.

### 3. **Product Management (`/products`, `/edit_product/<id>`, `/delete_product/<id>`)**:
   - Users can add new products with details such as name, price, place, quantity, weight, description, and image.
   - Upon upload, products are initially marked as `"under processing category"` and automatically classified by `backend.py` into `"organic"` or `"recycle"` using `model_small.h5`.

### 4. **AI Chat (`/ai_chat`)**:
   - Powered by `Qwen/Qwen2.5-0.5B` via `llmbackend.py`.
   - Provides a real-time chat interface where users can ask for practical, creative recycling and reuse ideas.

### 5. **Product Recommendations (`/recommend/<product_id>`)**:
   - Powered by `recommender.py`.
   - Computes a weighted hybrid similarity score (`0.7 * text_similarity + 0.3 * numeric_similarity`) to recommend the top 5 related products.

### 6. **Community Posts (`/community`, `/edit_community/<id>`, `/delete_community/<id>`)**:
   - Users can create, edit, and delete community posts for sustainability-related events or initiatives.
   - Supports multiple images, contact details, event location/time, and paginated browsing (6 posts per page).

### 7. **Owner-Based Permissions**:
   - Users can only edit or delete products and community posts that they have created.

## Folder Structure

```text
EcoShop/
│
├── app.py                                    # Main Flask application & route handlers
├── backend.py                                # CNN image classification & MongoDB category updater
├── llmbackend.py                             # Generative AI recycling idea assistant (Qwen2.5-0.5B)
├── recommender.py                            # Hybrid TF-IDF & numeric product recommendation engine
├── ml_processor.py                           # Standalone ML batch processor script
├── product_processor.py                      # Object-oriented ProductProcessor utility class
├── utils.py                                  # File validation & Base64 image encoding helpers
├── model_small.h5                            # Pre-trained CNN image classification model
├── requirements.txt                          # Python package dependencies
├── run.bat                                   # Windows batch launcher script
├── HARICHSELVAM_PROJECT_REPORT-2.docx.pdf    # Final Year B.Tech Project Report
├── static/                                   # Static files (CSS, images, etc.)
├── templates/                                # Jinja2 HTML Templates
│   ├── base.html
│   ├── home.html
│   ├── register.html
│   ├── login.html
│   ├── products.html
│   ├── edit_product.html
│   ├── recommendations.html
│   ├── community.html
│   ├── edit_community.html
│   └── ai_chat.html
└── training/                                 # Model training notebook, dataset & weights
    ├── DATASET/
    ├── app.ipynb
    └── organic_recycle_model.h5
```

## MongoDB Collections (`ecommerce_db`)

- **`users`**: Stores user account credentials (`username`, `email`, hashed `password`).
- **`products`**: Stores eco-friendly product listings (`name`, `price`, `place`, `quantity`, `weight`, `description`, `category`, `owner_id`, `owner_name`, `owner_email`, Base64 `image`).
- **`community_posts`**: Stores community-driven sustainability events (`event_name`, `place`, `time`, `description`, `contact_number`, `email`, `timestamp`, `user_id`, `username`, Base64 `images`).
- **`purchases`**: Stores user purchase records.

## AI Classification Model

The project uses a TensorFlow/Keras CNN model (`model_small.h5`) that classifies uploaded product images into `"organic"` (biodegradable) or `"recycle"` (recyclable).

### Model Details:
- **Model Type**: Convolutional Neural Network (CNN)
- **Input Size**: `80x45` pixels (RGB, normalized to `[0, 1]`)
- **Output Classes**: `['organic', 'recycle']`
