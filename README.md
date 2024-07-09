# Model Deployment Using Flask for Handwritten Digit Recognition
Flask is a lightweight WSGI web application framework. It is designed to make getting started quick and easy, with the ability to scale up to complex applications. It began as a simple wrapper around Werkzeug and Jinja, and has become one of the most popular Python web application frameworks.

This repository demonstrates how to deploy a machine learning model using Flask for recognizing handwritten digits. The deployed model predicts the digits(0 to 9) using convolutional neural network.

# Files:
### my_model.h5:
Hierarchical Data formatted machine learning model trained on the MNIST dataset.

### app.py:
Python script containing Flask web application code for model deployment.

## Templates:
HTML files for the web interface where users can input feature values and get predictions.
### index.html
```html
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>MNIST Digit Classification</title>
</head>
<body>
	<h1>Upload a Digit Image</h1>
	<form method="post" enctype="multipart/form-data">
		<input type="file" name="file" accept="image/*">
		<input type="submit" value="upload">
	</form>
</body>
</html>
```
### result.html
```html
<html>
	<head>
		<meta charset="UTF-8">
		<title>Prediction Result</title>
	</head>
<body>
	<h1>Prediction Result</h1>
	<p>The predicted digit is: {{ predicted_class }}</p>
	<a href="/">Go back</a>
</body>
</html>
```
# Requirements:
- [Python](https://github.com/python)

- [HTML](https://github.com/html)

- [Jupyter](https://github.com/jupyter)

- [Flask](https://github.com/flask)

- [Tensorflow](https://github.com/tensorflow)

- [keras](https://github.com/keras)

- [scikit-learn](https://github.com/scikit-learn)

- [numpy](https://github.com/numpy)

## License

Flask is completely free and open-source and licensed under the [BSD-3-Clause](https://flask.palletsprojects.com/en/2.3.x/license/) license.
