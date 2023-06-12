Validations Challenges
Create a Rails application called company_contacts. The app will have a PostgreSQL database.

Generate a model called Account that has a username, a password, and an email.
All stories should have accompanying model specs.

rails g model Account username:string password:string email:string

Developer Stories

As a developer, I need username, password, and email to be required.

validates :username, :password, :email, presence: true




As a developer, I need every username to be at least 5 characters long.
As a developer, I need each username to be unique.
As a developer, I need each password to be at least 6 characters long.
As a developer, I need each password to be unique.


RSpec.describe Account, type: :model do
  it 'has to be valid' do
    account = Account.create username: 'Jacob', password:'password', email:'example@email.com'
    expect(account.errors).to be_empty
  end
  it 'has to have a username' do
    account = Account.create password:'password', email:'example@email.com'
    expect(account.errors[:username]).to_not be_empty
  end
  it 'has to have a password' do
    account = Account.create username:'jacob', email:'example@email.com'
    expect(account.errors[:password]).to_not be_empty
  end
  it 'has to have a email' do
    account = Account.create username:'jacob', password:'password'
    expect(account.errors[:email]).to_not be_empty
  end
  it 'has to be at least 5 characters long' do
    account = Account.create username:'jac', password:'password'
    expect(account.errors[:username]).to_not be_empty
  end
  it 'has to be at least 6 characters long' do
    account = Account.create username:'jesus', password:'pass'
    expect(account.errors[:password]).to_not be_empty
  end
  it 'username has to be unique' do
    account = Account.create username:'jesus', password:'password', email:'example@email.com'
    account2 = Account.create username:'jesus', password:'password2', email:'example@email.com'
    Account.all
    expect(account2.errors[:username]).to_not be_empty
  end
  it 'password has to be unique' do
    account = Account.create username:'jesus', password:'password', email:'example@email.com'
    account2 = Account.create username:'jesus2', password:'password', email:'example@email.com'
    expect(account2.errors[:password]).to_not be_empty
  end
end



As a developer, I want my Account model to have many associated Addresses.

As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers.

rails g model Address street_number:integer street_name:'string' city:'string' state:'string' zip:integer

As a developer, I want to validate the presence of all fields on Address.

Stretch Challenges

As a developer, I need each Account password to have at least one number.
HINT: Read about custom validations in the Active Record validation docs.

class MyValidator < ActiveModel::Validator
    def validate(record)
        if record.password === nil
            record.errors.add :password, "password cannot be blank"
        
        else
            unless record.password.include? '1' || '2' || '3' || '4'|| '5'|| '6' || '7' || '8' || '9' || '0'
                record.errors.add :password, "password must contain a number"
             end
        end
    end
end

As a developer, I want to validate that Address street_number, street_name, zip are unique for within an account.


HINT: Read about :scope in the Active Record validation docs.
As a developer, I want to validate that the Address street_number and zip are numbers.
HINT: Read about numericality in the Active Record validation docs.
As a developer, I want to see a custom error message that says "Please, input numbers only" if street_number or zip code are not numbers.
HINT: Read about message in the validation docs



class Address < ApplicationRecord
    belongs_to :account
    validates :street_number, :street_name, :city, :state, :zip, :account_id, presence: {  message: 'gotta be unique breh' }
    validates :street_number, :zip, numericality: { only_integer: true,
    message: 'Please, input numbers only'}
    validates :street_number, :street_name, :zip, uniqueness: { scope: :account_id, message: 'There should only be one adress like that per account'}
end


class MyValidator < ActiveModel::Validator
    def validate(record)
        if record.password === nil
            record.errors.add :password, "password cannot be blank"
        
        else
            unless record.password.include? '1' || '2' || '3' || '4'|| '5'|| '6' || '7' || '8' || '9' || '0'
                record.errors.add :password, "password must contain a number"
             end
        end
    end
end

class Account < ApplicationRecord
    
    has_many :addresses
    validates :username, :password, :email, presence: true
    validates :username, length: { minimum: 5 }
    validates :password, length: { minimum: 6 }
    validates :username, :password, uniqueness: true
    validates :username, :password, uniqueness: true
    validates_with MyValidator
end




require 'rails_helper'

RSpec.describe Address, type: :model do
  it 'has to be valid' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:123545, street_name:'some road', city:'some city', state:'some state', zip:12345
    expect(address.errors).to be_empty
  end
  it 'has to have a street number' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_name:'some road', city:'some city', state:'some state', zip:12345
    expect(address.errors[:street_number]).to_not be_empty
  end
  it 'has to have a street name' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:123456, city:'some city', state:'some state', zip:12345
    expect(address.errors[:street_name]).to_not be_empty
  end
  it 'has to have a city' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:123545, street_name:'some road',  state:'some state', zip:12345
    expect(address.errors[:city]).to_not be_empty
  end

  it 'has to have a state' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:123545, street_name:'some road', city:'some city',  zip:12345
    expect(address.errors[:state]).to_not be_empty
  end

  it 'has to have a zip' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:123545, street_name:'some road', city:'some city', state:'some state'
    expect(address.errors[:zip]).to_not be_empty
  end
  it 'has to have a unique zip' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:1235456, street_name:'some road', city:'some city', state:'some state1',  zip:12345
    address2 = account.addresses.create street_number:123545, street_name:'some road', city:'some city', state:'some state',  zip:12345
    expect(address2.errors[:zip]).to_not be_empty
  end
  it 'has to have a unique street name' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:1235456, street_name:'some road', city:'some city1', state:'some state1',  zip:12345
    address2 = account.addresses.create street_number:123545, street_name:'some road', city:'some city', state:'some state',  zip:123451
    expect(address2.errors[:street_name]).to_not be_empty
  end
  it 'has to have a unique street number' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:123545, street_name:'some road1', city:'some city1', state:'some state1',  zip:12345
    address2 = account.addresses.create street_number:123545, street_name:'some road', city:'some city', state:'some state',  zip:123451
    expect(address2.errors[:street_number]).to_not be_empty
  end

  it 'has to have a whole number as street number' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    address = account.addresses.create street_number:'123545sdfg', street_name:'some road1', city:'some city1', state:'some state1',  zip:12345

    expect(address.errors[:street_number]).to_not be_empty
  end
    it 'has to have a number as zip' do
      account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
      address = account.addresses.create street_number:123545, street_name:'some road1', city:'some city1', state:'some state1',  zip:12345.2

      expect(address.errors[:zip]).to_not be_empty

  end


end

require 'rails_helper'

RSpec.describe Account, type: :model do
  it 'has to be valid' do
    account = Account.create username: 'Jacob', password:'password1', email:'example@email.com'
    expect(account.errors).to be_empty
  end
  it 'has to have a username' do
    account = Account.create password:'password1', email:'example@email.com'
    expect(account.errors[:username]).to_not be_empty
  end
  it 'has to have a password' do
    account = Account.create username:'jacob', email:'example@email.com'
    expect(account.errors[:password]).to_not be_empty
  end
  it 'has to have a email' do
    account = Account.create username:'jacob', password:'password1'
    expect(account.errors[:email]).to_not be_empty
  end
  it 'has to be at least 5 characters long' do
    account = Account.create username:'jac', password:'password1'
    expect(account.errors[:username]).to_not be_empty
  end
  it 'has to be at least 6 characters long' do
    account = Account.create username:'jesus', password:'pass'
    expect(account.errors[:password]).to_not be_empty
  end
  it 'username has to be unique' do
    account = Account.create username:'jesus', password:'password1', email:'example@email.com'
    account2 = Account.create username:'jesus', password:'password2', email:'example@email.com'
    Account.all
    expect(account2.errors[:username]).to_not be_empty
  end
  it 'password has to be unique' do
    account = Account.create username:'jesus', password:'password1', email:'example@email.com'
    account2 = Account.create username:'jesus2', password:'password1', email:'example@email.com'
    expect(account2.errors[:password]).to_not be_empty
  end
end
