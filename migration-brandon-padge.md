Add five entries to the database via the Rails console

Movie.create title: 'Princess Bride', category: 'Comedy'
Movie.create title: 'I Am Legend', category: 'Action'
Movie.create title: 'Zombieland', category: 'Comedy'
Movie.create title: 'World War Z', category: 'Action'
Movie.create title: 'Alien', category: 'Horror'

Create a migration to add a new column to the database called movie_length

rails g migration movie_length_column
rails db:migrate
    To check rails c => Movie.all

Update the values of the five existing attributes to include a movie_length value

princess_bride = Movie.find(1)
princess_bride.update movies_length:'1:38'
    Did for all 5.

Generate a migration to rename the column 'category' to 'genre'

rails g migration rename_column_category_to_genre
rails db:migrate