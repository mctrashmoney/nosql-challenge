# NoSQL Establishments Database

## Part One

### Importing - Data was imported to the terminal using the command
* Command
```shell
mongoimport --type json -d uk_food --collection establishments --drop --jsonArray establishments.json
```

## Part Two

### Updating the database
* The new restaurant was added in the [setup document](https://github.com/mctrashmoney/nosql-challenge/blob/main/Starter_Code/NoSQL_setup_starter.ipynb).
* The database was updated with the `BusinessTypeID`
* Dover documents were removed.
* Correct values were updated for `latitude`, `longitude`, and `RatingValue`.

## Part Three

### Analysis of the datafase in the [second document](https://github.com/mctrashmoney/nosql-challenge/blob/main/Starter_Code/NoSQL_analysis_starter.ipynb)
* First datafase created were hygiene scores of 20
* Second datafase created were establishments in London with a `RatingValue` `$gte`:4
* Third datafase displays the top 5 establishments with the lowest hygiene score near the new restaurant added.
  * Note: for the coordinates in this section, we simply look back at the previous document that displays it. If not, use this code and replace the integers for the variables for any other establishment to make it reusable.
```python
restaurant = establishments.find_one({"BusinessName": "Penang Flavours"}, {"geocode.latitude": 1, "geocode.longitude": 1})
latitude = restaurant["geocode"]["latitude"]
longitude = restaurant["geocode"]["longitude"]
```

## Part Four

### Each Local Authority dataframe
* The last dataframe displays the total amount of establishments in each Local Authority that have a hygiene score of zero.
* This was done with an aggregation pipeline, displaying the top ten results.

## Errors and lessons
* Learnt that cursors can only be used once after being iterated, which meant I had to rerun the code in a new cell. 
* Learnt the usefulness of a lambda function when working with a JSON file. Having nested data and cleaning it up will make this very useful in the future.