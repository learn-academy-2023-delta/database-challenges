Person.create(fist_name:"Amir", last_name:"Jackson", phone:"619=111=1111")
 id: 1,
 fist_name: "Amir",
 last_name: "Jackson",
 phone: "619=111=1111",
 created_at: Thu, 08 Jun 2023 19:01:23.283427000 UTC +00:00,
 updated_at: Thu, 08 Jun 2023 19:01:23.283427000 UTC +00:00>

Person.create(fist_name:"Jesus", last_name:"Camacho", phone:"619-222-2222")
id: 2,
 fist_name: "Jesus",
 last_name: "Camacho",
 phone: "619-222-2222",
 created_at: Thu, 08 Jun 2023 20:42:10.351327000 UTC +00:00,
 updated_at: Thu, 08 Jun 2023 20:42:10.351327000 UTC +00:00> 

 Person.create(fist_name:"Gene", last_name:"R", phone:"619-333-3333")
  id: 3,
 fist_name: "Gene",
 last_name: "R",
 phone: "619-333-3333",
 created_at: Thu, 08 Jun 2023 20:46:46.598730000 UTC +00:00,
 updated_at: Thu, 08 Jun 2023 20:46:46.598730000 UTC +00:00> 

 Person.create(fist_name:"A", last_name:"Camacho", phone:"619-444-4444")
 id: 4,
 fist_name: "A",
 last_name: "Camacho",
 phone: "619-444-4444",
 created_at: Thu, 08 Jun 2023 20:48:32.937928000 UTC +00:00,
 updated_at: Thu, 08 Jun 2023 20:48:32.937928000 UTC +00:00> 

 Person.create(fist_name:"B", last_name:"Camacho", phone:"619-555-5555")
 id: 5,
 fist_name: "B",
 last_name: "Camacho",
 phone: "619-555-5555",
 created_at: Thu, 08 Jun 2023 20:49:15.671176000 UTC +00:00,
 updated_at: Thu, 08 Jun 2023 20:49:15.671176000 UTC +00:00> 



Person.all


Person.where last_name:"Camacho"
 id: 2,
  fist_name: "Jesus",
  last_name: "Camacho",
  phone: "619-222-2222",
  created_at: Thu, 08 Jun 2023 20:42:10.351327000 UTC +00:00,
  updated_at: Thu, 08 Jun 2023 20:42:10.351327000 UTC +00:00>,
 #<Person:0x0000000107c76a48
  id: 4,
  fist_name: "A",
  last_name: "Camacho",
  phone: "619-444-4444",
  created_at: Thu, 08 Jun 2023 20:48:32.937928000 UTC +00:00,
  updated_at: Thu, 08 Jun 2023 20:48:32.937928000 UTC +00:00>,
 #<Person:0x0000000107c76908
  id: 5,
  fist_name: "B",
  last_name: "Camacho",
  phone: "619-555-5555",
  created_at: Thu, 08 Jun 2023 20:49:15.671176000 UTC +00:00,
  updated_at: Thu, 08 Jun 2023 20:49:15.671176000 UTC +00:00>] 


  Movie.create title:"Spiderman", category:"Action"
  Movie.create title:"Shrek", category:"Animated"
  Movie.create title:"Iron Man", category:"Action"
  Movie.create title:"Captain America", category:"Action"
  Movie.create title:"Nope", category:"Adventure"