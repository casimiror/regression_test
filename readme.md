

Challenge: Used Car Price Predictor
================================

The goal of this exercise is to develop a Python class that is able to fit a model to deliver predictions and recommendations about the prices of used cars in the US. In particular, these are the tasks that will be done:

- Load the downloaded dataset and prepare it for the modeling
- Fit a model to predict the prices of the given used cars
- Use the model to make single predictions, providing the top important features for each prediction 
- Run a service that loads the fitted model to make single predictions
- Provide endpoints to get predictions

The dataset to use contains records from residential used cars in the US, having variables to describe the property and the characteristics of the used car, including the price to be predicted. The following data dictionary helps to understand the meaning of each column:

| Variable | Description | 
| :------------- | :----------- |
| Make   |     The company maker of the car (categorical)|
| Model | The name of the car (categorical)|
| Type  | The type of Car (SUV, Sedan, etc) (categorical)|
| Origin  | Location the car was produced (categorical)|
| DriveTrain | Physical structure that connects the engine to the wheels enabling (categorical)|
| MSRP | Overall price (numerical) |
| EngineSize | Total volume of both fuel and air that can be pushed through a car's cylinder (numerical)|
| Cylinders | number of power units of the engine (numerical)|
| Horsepower | Amount of Power the engine generates  (numerical)|
| MPG_City | Miles per Gallon it consumes the car in city (numerical)|
| MPG_Highway | Miles per Gallon it consumes the car in city (numerical)|
| Weight | Wight of the car (numerical)|
| Wheelbase | distance between  front and rear wheels (numerical)|
| Length | Full length of the car (boolean)|

 The following Python snippet can be used as a reference of the intended usage of the asked class based on the mentioned tasks:

```python
# Ensure the class "used carScorerModel" is imported

# Create and fit a model using the downloaded dataset
hsm = UsedCarScorerModel("cars_data_11_19_23.csv")
hsm.fit()
# Get the performance of the fitted model
print(hsm.get_model_performance())
# > It should print a dict like {"train": {"rmae": 161.977, "mae": 26236.745}, "test": {...}}

# Get a single prediction with the top of important features for that prediction
data_point = {
    
    "model": "Acura",
    "type": "SUV",
    "origin": "Asia",
    "drive": "All",
    "msrp": "$36,945",
    "engine": "3.5",
    "cylinders": 6,
    "horsepower": 265,
    "mpg_city": 17,
    "mpg_highway": 23,
    "weight":451,
    "wheelbase": 106,
    "length": 189,
}
print(hsm.get_prediction(data_point))
# > It should print a dict like {"prediction": 162709.5, "top_features": {"used car_age": 0.712, "overall_quality": 0.221, ...}}
```

## Requirements

To accomplish the tasks mentioned, here are some requirements about the expected work to deliver:

- **Development:** Provide scripts / notebooks as desired, as long as the asked Python class can be tested based on the previous code snippet shown. 
- **Data Quality:** Analyze and control the quality of the data to be used to fit and evaluate the model.
- **Machine Learning:** Choose your favorite algorithm to train and validate a predictor model, selecting the metrics you consider appropriate to assess the performance. 
- **Environment:** Ensure you provide enough tools / information to reproduce the results in another machine.
- **Development:** : Deliver an app that serves the model through the following required endpoints:

    - /model_performance: GET endpoint to retrieve the performance of the trained model (no parameters).
        - Example of response: {"train": {"rmae": 161.977, "mae": 26236.745}, "test": {"rmae": 166.157, "mae": 27531.892}}
    - /predict: GET endpoint to retrieve a predicted price for a given house (where the parameters are the features used by the model).
        - Example of response: {"prediction": 162709.5}

## Extra points

The following aspects are NOT mandatory, but they will give an outstanding score of the work:

- *Model Explainability:* Report some insights about the interpretation of the model obtained and the predictions generated.
- *Code style:* Show good practices on the code developed (e.g. linting, documentation).
- *Testing:* Show at least some unit tests for the functions developed.

## Considerations

Make sure you have the following aspects in mind before starting:

- Feel free to decide the architecture and the way to design and deliver the asked Python class.
- Freedom for technologies, as long as everything is done in Python.
- Data Analysis capabilities will be evaluated, BUT it is not the main goal of the exercise. Make sure you spend more time in the asked tasks rather than in experimentation or deep analysis.
- Getting the best score possible won't be rated, as long as you can assess the performance of the model obtained.

This exercise was designed to be completed in ~6-8 hs, so it is OK to not achieve a perfect result since the idea is just to validate technical skills. If you have doubts, feel free to contact us to make everything clear for your work.
