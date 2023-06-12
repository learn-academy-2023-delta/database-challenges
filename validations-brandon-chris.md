As a developer, I need username, password, and email to be required.
For Each Column username/password/email

``` Ruby
it'is invalid with a password less than 6 characters' do
    it'is not valid without a username' do
    account = Account.create(password:'password', email:'123@yahoo.com')
    expect(account.errors[:username]).to_not be_empty
  end

  it'is not valid without a password' do
    account = Account.create(username:'username', email:'123@yahoo.com')
    expect(account.errors[:password]).to_not be_empty
  end

  it'is not valid without a email' do
    account = Account.create(username:'username', password:'password')
    expect(account.errors[:email]).to_not be_empty
  end


```

As a developer, I need every username to be at least 5 characters long.

``` Ruby
  it'is invalid with a username less than 5 characters' do
    account = Account.create(username:'use', password:'password', email:'123@yahoo.com')
    expect(account.errors[:username]).to_not be_empty
  end
```

As a developer, I need each username to be unique.

``` Ruby
it'is invalid if the username is not unique' do
    Account.create(username:'username', password:'password', email:'123@yahoo.com') 
    account = Account.create(username:'username', password:'password', email:'123@yahoo.com')
    expect(account.errors[:username]).to_not be_empty
  end
```

As a developer, I need each password to be at least 6 characters long.

``` Ruby
it'is invalid with a password less than 6 characters' do
    account = Account.create(username:'use', password:'pass', email:'123@yahoo.com')
    expect(account.errors[:password]).to_not be_empty
  end
```

As a developer, I need each password to be unique.

``` Ruby
it'is invalid if the password is not unique' do
    account1 = Account.create(username:'username', password:'password', email:'123@yahoo.com') 
    account = Account.create(username:'username', password:'password', email:'123@yahoo.com')
    expect(account.errors[:password]).to_not be_empty
  end
```

As a developer, I want my Account model to have many associated Addresses.
As a developer, I want Address to have street_number, street_name, city, state, and zip attributes. The street_number and zip should be integers.
As a developer, I want to validate the presence of all fields on Address.


``` Ruby
class Account < ApplicationRecord
    validates :username, :password, :email, presence:true
    validates :username, length: { minimum: 5 }
    validates :username, uniqueness: true
    validates :password, length: { minimum: 6 }
    validates :password, uniqueness: true
end
```