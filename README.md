# Lazy LazyPredict: An Exercise in Automated Python Libraries

[LazyPredict](https://pypi.org/project/lazypredict/) is an excellent python library that allows the user to automatically run their data through a myriad of models. It will then output information regarding how each model performed, allowing the user to view which model might be best for their use case.

This is a great tool to save time that might otherwise be spent manually testing different models. But while exploring this tool, I began to wonder what other manual steps I could accomplish purely with python libraries. And with that thought, I dove into a test of lazier than lazypredict predictions. After all:

![p_r_pizza_gif.gif](https://raw.githubusercontent.com/ismizu/Lazy_LazyPredict/main/images/p_r_pizza_gif.gif)

<h5 align = 'center'>
    Image from
    <a href = ' https://giphy.com/gifs/time-money-power-p6iPHyrGYLiRq'>
    Giphy.com
    </a>
</h5>

___

## Folder Structure

- Utilized data can be found in the /data folder, retrieved from [Kaggle.com](https://www.kaggle.com/c/titanic/overview)
- All images can be found in the /images folder

The following libraries will be used:
- [Lazy Predict](https://pypi.org/project/lazypredict/)
- [Feature Engine](https://pypi.org/project/feature-engine/)
- [Feature Tools](https://pypi.org/project/featuretools/)

## Cleaning the Data

Utilizing the MeanMedianImputer from Feature Engine:

- After importing the data, I utilize an automatic imputer to fill in missing values for Age.

![mean_impute.png](https://raw.githubusercontent.com/ismizu/Lazy_LazyPredict/main/images/mean_impute.png)

### Working with Extreme Values

I then utilize Feature Engine's Winsorizer to cap extreme values.

First, I take a look at the values. I then run the Winsorizer and recheck the values to view its effect.

![wins.png](https://raw.githubusercontent.com/ismizu/Lazy_LazyPredict/main/images/wins.png)

## Feature Engineering

Having done basic EDA, I'll now take a look at automated feature engineering with Feature Tools.

The first step will be to tell Feature Tools what each column datatype is. This will instruct it on how to create features from them. I'll also drop the Survived column and place it into a separate variable, as that is the value I am trying to predict.

![categories.png](https://raw.githubusercontent.com/ismizu/Lazy_LazyPredict/main/images/categories.png)

Next, I'll make an entity called survived. Feature Tools will utilize this to engineer new features.

I also create relationship that I would like Feature Tools to explore.

![entities.png](https://raw.githubusercontent.com/ismizu/Lazy_LazyPredict/main/images/entities.png)

Having now set the relationships, I can run Feature Tool's Deep Feature Synthesis to engineer new features.

![feature_engineering.png](https://raw.githubusercontent.com/ismizu/Lazy_LazyPredict/main/images/feature_engineering.png)

## Testing Models with Lazy Predict

Finally, I'll instantiate the LazyClassifier and run it using a train/test split.

After running, it creates the following table:

![lazy_predict.png](https://raw.githubusercontent.com/ismizu/Lazy_LazyPredict/main/images/lazy_predict.png)

# Final Notes

Utilizing Feature Tools, Feature Engine, and Lazy Predict, I was able to naarrow down to utilizing Logistic Regression for my model as well as being able to utilize a slew of engineered features.

There were a few items I would have liked to look further into, but I felt they broke the spirit of using the three libraries for nearly 100% of the EDA/feature engineering process. Overall, I found this a great exercise in utilizing the three libraries and feel that, with a little more tweaking and practice, would be great additions to my usuaal data analysis process.
