As a user, I can see the names of my team members as hyperlinks on the landing page.

    Rails.application.routes.draw do
        root 'pages#membersnames'
        get '/Paul' => 'pages#paul_method'
        get '/Jacob' => 'pages#jacob_method'
        get '/cubed/:number' => 'pages#cubed_method'
        get '/even/:number/:number1' => 'pages#even_method' 
        get '/palindrome/:string' => 'pages#palindrome_method'
        get 'madlib/:noun/:verb/:adjective/:adverb' => 'pages#madlib_method'
    end



    class PagesController < ApplicationController
        def membersnames
       
        end

        def paul_method
        end

        def jacob_method
        end

        def cubed_method 
            @number = params[:number]
        end

        def even_method
            @number = params[:number]
            @number1 = params[:number1]
        end

        def palindrome_method
            @string = params[:string]
        end

        def madlib_method
            @noun = params[:noun]
            @verb = params[:verb]
            @adjective = params[:adjective]
            @adverb = params[:adverb] 
        end
    end

As a user, I can see the names of my team members as hyperlinks on the landing page.

    <h1>Hello World Views</h1> 
    <%= link_to 'Paul Gooden', '/Paul' %>
    <%= link_to 'Jacob Oakley', '/Jacob' %>

    <h1>Pauls Page</h1>
    <%= link_to 'Home', '/' %>

    <h1>Jacobs Page</h1>
    <%= link_to 'Home', '/' %>

As a user, I can visit a page called cubed that takes a number as a param and displays that number cubed.

    h1><%= @number.to_i**3%></h1>

As a user, I can visit a page called evenly that takes two numbers as params and displays whether or not the first number is evenly divisible by the second.

    <% if @number.to_i % @number1.to_i == 0 %> 
    <h1> the numbers are evenly divisible. </h1>
    <% else %>
    <h1>the numbers are not evenly divisible.</h1>
    <% end %>

As a user, I can visit a page called palindrome that takes a string as a param and displays whether it is a palindrome (the same word forward and backward).

    <% if @string.downcase == @string.reverse.downcase %>
    h1> the word is a palindrome. </h1>
    <% else %>
    <h1>the word is not a palindrome.</h1>
    <% end %>

As a user, I can visit a page called madlib that takes params of a noun, verb, adjective, adverb, and displays a short silly story.

    p>the <%= @noun %> jumped over the hat</p>
    <br>
    <br>
    <p>the cat <%=  @verb %> over the hat</p>
    <br>
    <br>
    <p>the cat <%= @adverb %> jumped over the hat</p>
    <br>
    <br>
    <p>the cat jumped over the <%=  @adjective %> hat</p>