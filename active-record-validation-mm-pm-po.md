# Validations Challenges

Create a Rails application called company_contacts. The app will have a PostgreSQL database.

Generate a model called Account that has a username, a password, and an email.
All stories should have accompanying model specs.


# Developer Stories

# As a developer, I need username, password, and email to be required.

class Account < ApplicationRecord
    validates :username, :password, :email presence: true
end

# As a developer, I need every username to be at least 5 characters long.

class Account < ApplicationRecord
    validates :username, length: { minimum: 5 }
    validates :password, presence: true
    validates :email, uniqueness: true
end

# As a developer, I need each username to be unique.
 
 class Account < ApplicationRecord
    validates :username, length: { minimum: 5 }, uniqueness: true
    validates :password, presence: true
    validates :email, uniqueness: true
end

# As a developer, I need each password to be at least 6 characters long.
 
 class Account < ApplicationRecord
    validates :username, length: { minimum: 5 }, uniqueness: true
    validates :password, presence: true, length: { minimum: 6..30 }
    validates :email, uniqueness: true
end

# As a developer, I need each password to be unique.



# As a developer, I want my Account model to have many associated Addresses.


# As a developer, I want Address to have street_number, street_name, city, state, and 
zip attributes. The street_number and zip should be integers.


# As a developer, I want to validate the presence of all fields on Address.


# TESTING

require 'rails_helper'

RSpec.describe Account, type: :model do
  it 'is valid with valid attributes' do 
    account = Account.create(username: 'moneyman', password:'makinggreens', email:'stackit@gmail.com')
    expect(account).to be_valid

end
  it 'is not valid without a username' do 
    account = Account.create(password: 'moneyman', email:'stackit@gmail.com')
    expect(account.errors[:username]).to_not be_empty
    end

  it 'is not valid if less than 5 characters' do 
    account = Account.create(username: 'D')
    expect(account.errors[:username]).to_not be_empty
  end

  it 'is not valid if username is not unique' do 
    Account.create(username: 'moneyman', password:'makinggreens', email:'stackit@gmail.com')
    account1 = Account.create(username: 'moneyman2', password:'makinggreens', email:'stackit@gmail.com')

    expect(account1.errors[:username]).to_not be_empty
  end
  it 'is not valid if password is not unique' do 
    Account.create(username: 'moneyma11n', password: 'makinggreens', email:'stackit@gmail.com')
    account1 =  Account.create(username: 'moneyman', password: 'makinggreens', email:'stackit@gmail.com')
    expect(account1.errors[:password]).to_not be_empty
  end

end



# validations

class Account < ApplicationRecord
    validates :username, presence: true, length: { minimum: 5 }, uniqueness: true
    validates :password, presence: true, uniqueness: true
    validates :email, uniqueness: true
end