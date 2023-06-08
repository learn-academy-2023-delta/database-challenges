This is us documenting this shit

We created the rails app using rails new
We cd into the folder
created a database using rails db create
then we generated a model class using rails generate model 
1. Now we are adding five people to the db using Person.create
2. We used person.all to get all family members from the db
3. We use Person.create to add myself to the data pool
4. We used Person.where(last_name: 'Mattaliano') to retrieve all persons with the same last name 
5. Use update_last.update(phone: '858-423-8383') to give the person their phone number
6. We then used Person.select(:first_name).find(3) to find the first name of the third person


