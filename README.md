# COMP560 Final Project

#### Authors: Abdulaziz Al-Shayef, Nabeel Abdul Rahman

Some of the files in our project were too big to get uploaded to github. We have a file called FinalProjectResources.md that contains a video demonstrating the project, as well as a link to the Google Drive folder that contains all the code, essentially our repository. 


Below is the abstract that was submitted as part of the mid-semester check-in. 

### Cultural Cooking Assistant

As a college student, times can get busy and figuring out what to cook for dinner can add unncessary stress to the day. Also, isn't that same bowl of chicken and rice with broccoli just getting old? It's time to make finding new foods to make easier and more fun!

Our goal is to train a cooking assistant that will assist students with finding recipes with what they already have! We will leverage NLP and language models to accomplish our goals:

1. Analyze recipe ingredients
2. Generate *context-aware* cooking instructions
3. Modify existing recipes to integrate different cultures into the same dish.

By combing NLP techniques such as; tokenization and TF-IDF vectorization, we aim for a system that can both accurately and reliabley reccomend and modify different types of recipes.

We feel as if this would be an appropriate project because, as stated before, college students tend to struggle to figure out what to eat. Also, part of the college experience is meeting different types of people and being immersed in different cultures! We aim for this to be able to be a connective layer between friends and peers to experience and bring together different types of cultures.

#### Minimum Viable Goal
Our minimum viable goal would be for a user to enter a list of ingredients that they currently have or would like to use and the Cooking Assistant will be able to provide recipe(s) containing the ingredients!

#### Expected Goals

Our first goal is to be able to enter a list of ingredents and a type of cuisine that will help in the filtering process or types of recipes that will be outputted to the user.

Our second goal is to ask for a recipe with a cultural influence/spin on it. I.e. "Buldak Ramen" is a popular Korean dish. A user will be able to request an "Indian" influence on the recipe, which for example, could change the way the chicken is seasoned or the way the broth is prepared, etc.

### Process

Provided below is a detailed explanation, with steps of a high overview approach on how we will accomplish our goals.

##### Step 1
**Dataset Collection**

We will acquire our data from the popular [Kaggle](https://www.kaggle.com/datasets/kaggle/recipe-ingredients-dataset/data?select=train.json) website that has thousands of recipes. The data will be useful here as each recipe is an object containing a **cuisine** and **list of ingredients**.

Our data will need to be properly preprocessed. Standarized data will allow more effictive usage by our NLP pipeline. Using tools such as *pandas* and *NLTK* will allow for us to gather and convert our recipes into tokens.  

##### Step 2
**Ingredient-Based Retrieval**
Stated by our minimum viable goal, a user should be able to input a list of ingredients and expect real recipes that use those ingredients to be outputted!

Using vectorization, we can convert our recipes into numerical vectors to be processed by our assisstant. We will be using the Term Frequency–Inverse Document Frequency (TF-IDF) method in order to construct a domain-frequent association between all ingredients.

##### Step 3
**Cultural Pattern**
Stated by our reach goal for the project, we must be able to tie certain ingredients with certain cuisines. 

We will first construct a frequency table that will count the ingredients by cuisine. This will allow for association rule mining (*apriori algorthm*) to be applied in order to create associations between ingredients within a culture. I.e. "If a recipe has cumin and tumeric in it, it often has garam masala as well." This is important for the cultural spin feature we would like our assistant to have.

We also hope to use Word2Vec here in order to find semantic similarities and strengthen the substitutes provided by the Cooking Assistant!


##### Step 4
**Generating Recipe**

GPT-2 has already been trained on copious amounts of internet text and it already has general knowledge and great English syntax. We hope to successfully fine-tune the model in order to strenghten its ability to generate recipe instructions. We will do this by feeding the model our recipe data, continuously strengthening its ability to produce recipe-like outputs.

***Note: we will be using a smaller GPT-2 model***

##### Step 5
**Cultural Substituion**

Stated by our second reach goal, a user should be able to put a different cultural influence on a recipe.

We will begin by building a substitution table between popular ingredients that will be rule-based. I.e. *mirin -> yogurt* or *noodles -> rice*. Word2Vec will be used in order to automatically discover these associations. With these associations, specific ingredients that are tied with a single cuisine, will be replacable by the user's desirable cuisine.
