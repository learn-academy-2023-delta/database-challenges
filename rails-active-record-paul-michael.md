// Generate a model called Person with a first_name, last_name, and phone. All fields should be strings.

$ rails generate model Dog name:string breed:string age:integer

rails generate model Person first_name:string last_name:string phone:string

// Run a migration to set up the database.

rails db:migrate

// Open up Rails console.

$ rails c

Actions

Add five family members into the Person table in the Rails console.

Person.create first_name: "Chistopher",last_name: "Wallace", phone: "619-918-4163" 
Person.create first_name: "Roxanne",last_name: "Shantelle", phone: "619-918-4163" 
Person.create first_name: "Clifford",last_name: "Smith", phone: "619-918-4163" 
Person.create first_name: "Marshall",last_name: "Mathers", phone: "619-918-4163" 
Person.create first_name: "DeWayne",last_name: "Carter", phone: "619-918-4163" 

Retrieve all the items in the database.

Add yourself to the Person table.

Retrieve all the entries that have the same last_name as you.

Update the phone number of the last entry in the database.

Retrieve the first_name of the third Person in the database.


Stretch Challenges

Update all the family members with the same last_name as you, to have the same phone number as you.

Remove all family members that do not have your last_name.
