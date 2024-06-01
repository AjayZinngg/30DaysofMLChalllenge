# Recommendation System for Booking.com Dataset

## Problem Statement

The objective of this project is to develop a machine learning model capable of predicting the last destination in a multi-destination trip using the Booking.com dataset. This system aims to enhance the travel planning experience by providing accurate predictions of the next travel destination based on previous trip data.

## Dataset Overview

The dataset comprises anonymized booking data from Booking.com, including:
- **Train Set**: Training data featuring multiple destinations per trip.
- **Test Set**: Test data with the last destination concealed to evaluate the model's prediction accuracy.
- **Ground Truths**: Actual last destinations for the test set data to validate model predictions.

### Data Features
- `user_id`: Unique identifier for the user.
- `checkin`, `checkout`: Check-in and check-out dates for reservations.
- `created_date`: Date when the booking was made.
- `affiliate_id`: Anonymized ID representing the affiliate channels.
- `device_class`: Device type used for booking (desktop or mobile).
- `booker_country`, `hotel_country`: Anonymized country information for the booker and the hotel.
- `city_id`: Anonymized city identifier for the hotel's city.
- `utrip_id`: Unique identifier for each trip consisting of multiple destinations.

## Data Preprocessing

Data preprocessing includes:
- **Sampling**: A fraction of the data is used for analysis due to computational constraints.
- **Date Handling**: Conversion of date fields to datetime format to facilitate date-based calculations.
- **Sorting**: Data is sorted by `utrip_id` and `checkin` to preserve the chronological order of bookings.
- **NaN Handling**: Missing values are filled with 'Unknown' to prevent processing errors.

## Modeling Approaches

### LSTM Model
The LSTM model leverages the sequential nature of the data, using the following architecture:
- **Embedding Layer**: To convert city identifiers into dense vectors.
- **Bidirectional LSTM**: Captures dependencies in both directions of the sequence for better context understanding.
- **LSTM Layer**: Additional LSTM layer for capturing complex patterns.
- **Output Layer**: Dense layer with softmax activation to predict the probability distribution over potential destinations.

### RNN Model
A simple RNN model is also used to compare performance with the LSTM model:
- **Embedding Layer**: Similar to the LSTM model for handling categorical input.
- **Simple RNN Layer**: Processes the sequence data to capture temporal relationships.
- **Output Layer**: Outputs the next possible destination using a softmax function.

## Cross-Validation
Both models are evaluated using K-Fold cross-validation to ensure that the model's performance is robust and not dependent on the particular way the data is split.

## Training and Evaluation
- **Compilation**: Both models are compiled with the Adam optimizer and sparse categorical crossentropy loss function, suitable for multi-class classification.
- **Training**: The models are trained on the processed sequences, with model checkpoints saved based on validation accuracy.
- **Metrics**: Model performance is assessed using accuracy and precision metrics.

## Conclusion
This project demonstrates the application of LSTM and RNN models to predict the next destination in a travel sequence. The models are designed to improve the accuracy of recommendations, providing valuable insights for enhancing user experience in travel planning platforms like Booking.com.

## Output
The final predictions and model evaluations are saved and documented for further analysis, allowing for continuous refinement and deployment of the models in production environments.

