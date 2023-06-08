--Create a new Rails application called 'favorite_movies'.
$rails new favorite_movies -d postgresql -T

--Create the database
$rails db:create

--Generate a Movie model with a title attribute and a category attribute
$ rails generate model Movie title:string category: string
$ rails db:migrate => to migrate to Schema do it in a separate console. inside of the the app folder. Also you need a change to migrate.

Challenges
--Add five entries to the database via the Rails console
$ rails c => to be in the console

Movie.create title: "The Dark Knight", category: "Action"

Movie.create title: "Water Boy", category: "Comedy"

Movie.create title: "8 Mile", category: "Drama"

Movie.create title: "Major Payne", category: "Comedy"

Movie.create title: "Aliens", category: "Sci-fi"

--create a migration to add a new column to the database called movie_length

add_column :movies, :movie_leght, :string
rails g migration add_column_movie_length_Movie

Update the values of the five existing attributes to include a movie_length value

Generate a migration to rename the column 'category' to 'genre'
