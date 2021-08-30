# Deploying a Bank Note Authentication model using Flasgger
## This problem is part of Kaggle: https://www.kaggle.com/ritesaluja/bank-note-authentication-uci-data
### The objective of the problem is to distinguish between forged bank notes and authentic notes. The data comprises of 4 features and 1 target columns, and then create a Flask App which can be invoked via POSTMAN or localhost.

#### The features are: 'variance', 'skewness', 'kurtosis', and 'entropy'. The target column is labelled as 'class'.

The features were extracted from images that were taken from genuine and forged banknote-like specimens. For digitization, an industrial camera, usually used for print inspection was used. The final images have 400x 400 pixels. Due to the object lens and distance to the investigated object, gray-scale pictures with a resolution of about 660 dpi were gained. Wavelet Transform tool were used to extract features from images.

This is a simple classification problem without much requirement for feature engineering. With a default RandomForest Classifier model, we were able to achieve >99% validation accuracy. The trained model is then saved as a .pkl file (classifier.pkl) for later use.

In this scenario, we use Streamlit to render a new webpage using the template provided, and then deploy this entire framework on Heroku to have a anytime available web-based application. Thus Heroku helps us leverage Cloud services for deployment, while Streamlit helps in creating a webpage for interaction with the web-app in both a developer-friendly, as well as a user-friendly way. The app.py structure is still same, invoking a predict_note_authentication() with the features extracted from the Streamlit based web-page, to loading the pre-trained model (saved as classifier.pkl) to provide the prediction.

To run this, we need to execute this app.py file using StreamLit from CLI, using the command "streamlit run api.py", when running locally. However, as in this case we will be run through Heroku, so some additonal changes will be needed.

We need to create the below files:
1. setup.sh: This is a bash file, which helps create our StreamLit environment on Heroku.
2. procfile: This is a standard file required for Heroku deployment, telling how to deploy the application and which methods to execute. we mention here that we wish to run the "setup.sh" file and thereon we wish to run the command "streamlit run app.py" like we were running when executing the app locally
3. requirements.txt: once again a standard Heroku deployment file, highlighting the environmental requirements for running the python app on Heroku instance.
