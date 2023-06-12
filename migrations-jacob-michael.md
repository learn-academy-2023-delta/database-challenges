Setup
--Create a new rails application and database

$rails new credit-name  -d postgresql -T ==> creates app without db adding PostgreSQl without the testing frame

$rails db:create ==> create data a base


--Create a model for owner

An owner has a name and address, and can have multiple credit cards
Create a model for credit card
$ rails g model Owner name:string address:string

A credit card has a number, an expiration date, and an owner
Challenges
$ rails g model Card  number:string expiration_date:string owner_id:integer
$ rails db:migrate ==> migrate the models

Created the ralationship of the models within the app/models/name_of_file folder with has_many and belongs_to with rails helpers

--Create three owners and save them in the databas
       Owner.create(name:'Jacob', address:'Random address one')
       Owner.create(name:'Michael', address:'Random address two')
       Owner.create(name:'Miguel', address:'Random address three')

--Create a credit card in the database for each owner

 Owner.find(1).cards.create(number:'102554111', expiration_date: '51215411')


Add two more credit cards to one of the owners
Stretch Challenge
Add a credit limit to each card
Find the total credit extended to the owner with multiple credit cards
