Routes, Views, Controllers

As a user, I can visit a custom landing page at localhost:3000.
As a user, I can see the names of my team members as hyperlinks on the landing page.
As a user, I can click on each team member's name and be taken to a page that displays a list of that team member's top three things. (Could be top three restaurants, activities, books, video games, hiking locations, beaches, doughnut shoppes, movies, etc.)
Params
As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.
As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.
As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).
As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.

``` Ruby
class LandingController < ApplicationController
    def landing_page 
   
    end

    def brandon_list
        @list = 'Books, Cars, Sports'
        render 'brandon_list'
       
    end

    def michael_list
        @list = 'Books, Games, Cars'
        render 'michael_list'
       
    end

    def jesus_list
        @list = 'Books, Games, Sports'
        render 'jesus_list'
       
    end

    def cubed
        @number = params[:number]
        @multiple = @number.to_i**3
        return @multiple.to_s
    end

    def evenly
        @number = params[:number1]
        @number2 = params[:number2]
        @answer = "#{@number} is evenly divisible by #{@number2}"
        if @number.to_i % @number2.to_i == 0
            @answer
        elsif
            @answer = "#{@number} is not evenly divisible by #{@number2}"
        end

    end

    def palindrome
        @word = params[:string]
        @answer = "#{@word} is a palindrome"
        if @word == @word.reverse
            @answer = "#{@word} is a palindrome"
        elsif
            @answer = "#{@word} is a not palindrome"
        end

    end

    def madlib
        @p1 = params[:noun]
        @p2 = params[:verb]
        @p3 = params[:adverb]
        @p4 = params[:adjective]
    end

end
```

``` Ruby
Rails.application.routes.draw do
root 'landing#landing_page'

  get '/jesus' => 'landing#jesus_list'

  get '/brandon' => 'landing#brandon_list'

  get '/michael' => 'landing#michael_list'

  get '/cubed/:number' => 'landing#cubed'

  get 'evenly/:number1/:number2' => 'landing#evenly'

  get 'palindrome/:string' => 'landing#palindrome'
 
  get 'madlib/:noun/:adverb/:verb/:adjective' => 'landing#madlib'

end

```

Made Multiple files.html.erb within app/views/landing for our routes.
Went into the .erb files and used html tags while calling upon ruby params to finish challenges.