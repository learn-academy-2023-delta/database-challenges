As a developer, I have been tasked with creating a database model that will be used in a rolodex application. I want to ensure that the database behaves as expected and the necessary actions can be performed on the database instances.



Set Up

We did more than just make the rolodex, but we forgot to put most of it in this file.

Create a new Rails app named 'rolodex_challenge'.


Create the database. The output in the terminal should look like this:
Created database 'rolodex_development'
Created database 'rolodex_test'
Generate a model called Person with a first_name, last_name, and phone. All fields should be strings.
Run a migration to set up the database.
Open up Rails console.


---------
Setup
Create a new Rails application called 'favorite_movies'.
Create the database
Generate a Movie model with a title attribute and a category attribute -
Challenges 
Add five entries to the database via the Rails console -

Create a migration to add a new column to the database called movie_length
Update the values of the five existing attributes to include a movie_length value -
Generate a migration to rename the column 'category' to 'genre'


$ rails new favorite_movies -d postgresql -T
$ favorite_movies 
$ rails db:create
$ rails server


rails g model Movie title:string category:string

rails db: migrate

Movie.create title: "Fight Club", category: "Awesome"
Movie.create title: "The Goonies", category: "Adventure Movie"
Movie.create title: "Ferris Bueller's Day Off", category: "Playin Hooky"
Movie.create title: "The Breakfast Club", category: "Coming of Age"
Movie.create title: "Pineapple Express", category: "Munchies"

 % rails g migration add_column_to_movie_database
rails db:migrate

Book.where(category: "Ruby")

Movie.find_by(title: "Fight Club").update(movie_length: "2 hr 30 min")
Movie.find_by(title: "The Goonies").update(movie_length: "2 hr 15 min")
Movie.find_by(title: "Ferris Bueller's Day Off").update(movie_length: "2 hr 45 min")
Movie.find_by(title: "The Breakfast Club").update(movie_length: "2 hr 00min")
Movie.find_by(title: "Pineapple Express").update(movie_length: "1 hr 45 min")


rails g migration change_category_column_to_genre
class ChangeCategoryColumnToGenre < ActiveRecord::Migration[7.0]
  def change
    rename_column :movies, :category, :genre
  end
end
rails db:migrate