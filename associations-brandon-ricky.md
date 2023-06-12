Create three owners and save them in the database
``` ruby
Owner.create name:'Ricky', address:123 Elmo St.
Owner.create name:'Brandon', address:124 Elmo St.
Owner.create name:'John', address:125 Elmo St.
```
Create a credit card in the database for each owner
Add two more credit cards to one of the owners
``` ruby
ricky.credit_cards.create number:'1111-1111-1111-1111', expiration_date:'01/24'

```

Stretch Challenge
Add a credit limit to each card
Find the total credit extended to the owner with multiple credit cards
