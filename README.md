# Model Deployment Using Flask for Handwritten Digit Recognition
Flask is a lightweight WSGI web application framework. It is designed to make getting started quick and easy, with the ability to scale up to complex applications. It began as a simple wrapper around Werkzeug and Jinja, and has become one of the most popular Python web application frameworks.

This repository demonstrates how to deploy a machine learning model using Flask for recognizing handwritten digits. The deployed model predicts the digits(0 to 9) using convolutional neural network.

# Files:
### my_model.h5:
Hierarchical Data formatted machine learning model trained on the MNIST dataset.

### app.py:
Python script containing Flask web application code for model deployment.
```python
from flask import Flask,request,render_template
import tensorflow as tf
from tensorflow.keras.models import load_model
import numpy as np
from PIL import Image,ImageOps

app=Flask(__name__)

model=load_model('my_model.h5')

def prepare_image(image):
    image=ImageOps.grayscale(image) #gray_scaling
    image=ImageOps.invert(image) #to read images from black&white backgrounds
    image=image.resize((28,28))
    image=np.array(image)/255
    image=image.reshape(1,28,28,1)
    return image

@app.route('/',methods=['GET','POST'])
def index():
    if request.method=='POST':
        file=request.files['file']
        if file:
            image=Image.open(file.stream)
            image=prepare_image(image)
            prediction=model.predict(image)
            predicted_class=np.argmax(prediction)
            return render_template('result.html',predicted_class=predicted_class)
    return render_template('index.html')

if __name__=='__main__':
    app.run(debug=True,use_reloader=False)
```

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

- [VS Code](https://github.com/microsoft/vscode)

- [Flask](https://github.com/flask)

- [Tensorflow](https://github.com/tensorflow)

- [keras](https://github.com/keras)

- [scikit-learn](https://github.com/scikit-learn)

- [numpy](https://github.com/numpy)

## License

Flask is completely free and open-source and licensed under the [BSD-3-Clause](https://flask.palletsprojects.com/en/2.3.x/license/) license.
