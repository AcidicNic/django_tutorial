1. What does a model’s field type represent? If I use a CharField versus a TextField, for example, what does that change about how the data is stored?
    * A CharField is can hold a max of 255 characters. While a TextField can hold over 255 characters.

2. What is the difference between the null and blank field options? What do each of them represent?
    * 'blank' is false if you want the form element to be required, or true if empty values are allowed.
    * If 'null' is true, blank values will be stored in the database as null.

3. How do we use the TextChoices field type to display multiple options?
    * We first define: varname = models.TextChoices('<varname>', 'choice1 choice2 choice3')
    * Then we set the 'choices' field equal to the var we created above.

4. What is a primary_key field? If we don’t specify a primary key, what is the default?
    * If the primary_key field is set to true, the value from this form element will be used as the primary key (ID) in the database. Otherwise, a random integer will be generated and used as the primary key.

5. How do we specify a verbose name? What purpose does it serve?
    * We can include a string that will be the verbose name, otherwise Django will automatically create the name from the variable's name.

6. In the documentation under “Many-to-one Relationships”, an example is given of “Manufacturer” and “Car” models. Complete the code by adding at least 2 new fields to each model.
    ```
    class Manufacturer(models.Model):
        name = models.CharField(max_length=30)
   
    class Car(models.Model):
        year = fields.IntegerRangeField(min_value=1900, max_value=2020)
        company_that_makes_it = models.ForeignKey(Manufacturer, on_delete=models.CASCADE)

7. In the documentation under “Many-to-Many Relationships”, an example is given of “Pizza” and “Topping” models. Complete the code by adding at least 2 new fields to each model.
    ```
    class Topping(models.Model):
        title = models.CharField(max_length=30)
    
    class Pizza(models.Model):
        crust_type = models.CharField(max_length=20)
        toppings = models.ManyToManyField(Topping)

8. What is an example of a one-to-one relationship? When would we use a OneToOneField?
    * A profile can have one profile picture and every profile picture belongs to one profile.

9. Sometimes we need to relate a model to one from another app. Give an example of an import line to show how we’d import the other model.
    * from <app_name>.models import <model name>

10. What is the class Meta? When would we use it?
    * The meta class is used to store information that isn't grabbed from a form.

11. What is an example of a model method? Suppose we have a class Album. What methods might we want to write for it?
    * we could add a __str__(self) method to return a string with some formatted info about the album.

12. Give an example of model inheritance. How does inheritance help us to write better code?
    * Inheritance helps us keep our code DRY. You may need a model in one app that's similar to one you've already written. Inheritance keeps us from repeating code.
