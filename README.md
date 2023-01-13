#### Crowdfunding Project

# GoodGo

![](img/logo.png)

GoodGo is a crowdfunding platform that aims to support the Ukrainian people and their fight against Russian aggression. The platform is designed to connect individuals and organizations who wish to make a difference in the community by supporting projects and initiatives that address the challenges caused by the ongoing conflict. The platform targets volunteers who are actively working to restore normalcy in the de-occupied territories, providing assistance to those affected by the conflict, and supporting the efforts of those who are fighting to defend democratic values, human rights, and peace. GoodGo is a great way for people to make a real impact in the community and to support the Ukrainian people in their time of need. Whether it's by donating, volunteering, or starting their own project, GoodGo empowers individuals to make a difference.

### The features my MVP will include:

- Ability to create, login/logout user accounts
- Ability to create a “project” to be crowdfunded
- Project listing and browsing
- Ability to “pledge” to a project
- Implement suitable update/delete projects functionality

### Additional features I would like to include:

- Commenting system - would allow users to leave comments on projects. This feature could also be used as a way of answering questions and doubts.
- Search function - would allow users to search for projects based on keywords
- Add the ability to “favourite” project and see a page with your favourite projects.

### An API specification:

#### Register a new user

- /users/register
- Method: POST
  Request Body:

```
{
    "username": "johndoe",
    "email": "johndoe@example.com",
    "password": "password123"
}
```

Success Response:
Code: 201
Content:

```
{
    "id": 1,
    "username": "johndoe",
    "email": "johndoe@example.com"
}
```

#### Login a user

- /users/login
- Method: POST
  Request Body:

```
{
    "email": "johndoe@example.com",
    "password": "password123"
}
```

Success Response:
Code: 200
Content:

```
{
    "token": "..."
}
```

#### Get user info

- /user/:id
- Method: GET
  Success Response:
  Code: 200
  Content:

```
[
    {
       "id": 1,
        "username": "johndoe",
        "email": "johndoe@example.com"
    }
```

#### Edit user info

- /user/:id
- Method: PATCH

#### Get all projects

- /projects
- Method: GET
  Success Response:
  Code: 200
  Content:

```
[
    {
        "id": 1,
        "user_id": 1,
        "title":
```

#### Create a new project

- /projects
- Method: POST
  Headers:

```
{
    "Authorization": "<access_token>"
}
```

Request Body:

```
{
    "title": "Help Build a Community Garden",
    "image": "https://www.tweed.nsw.gov.au/files/assets/public/images/property-and-rates/pets-and-livestock/cats/cat.jpg?dimension=pageimage&w=480",
    "description": "We want to build a community garden in our neighborhood to provide fresh produce for local families."
}
```

Success Response:
Code: 201
Content:

```
{
    "id": 1,
    "user_id": 1,
    "title": "Help Build a Community Garden",
    "image": "https://www.tweed.nsw.gov.au/files/assets/public/images/property-and-rates/pets-and-livestock/cats/cat.jpg?dimension=pageimage&w=480",
    "description": "We want to build a community garden in our neighborhood to provide fresh produce for local families.",
    "date": "2022-12-31"
}
```

#### Edit project

- /projects/:id
- Method: PATCH

#### Delete project

- /projects/:id
- Method: DELETE

#### Create a new pledge

- /pledges
- Method: POST

#### Get pledges

- /pledges
- Method: GET

#### Edit pledge

- /pledges/:id
- Method: PUTCH

#### Delete pledge

- /pledges/:id
- Method: DELETE

### A database schema:

```mermaid

classDiagram
direction RL
Project <|-- User
User --|> Pledge
Pledge <|--|> Project
class Project{
id (INTEGER, primary key)
user_id (INTEGER, foreign key to USER.id)
title (STRING)
image (STRING)
description (STRING)
date (DATETIME)
}
class User{
id (INTEGER, primary key)
username (STRING)
email (STRING)
password (STRING)
}
class Pledge{
id (INTEGER, primary key)
user_id (INTEGER, foreign key to USER.id)
project_id (INTEGER, foreign key to PROJECT.id)
amount (INTEGER)
anonymous (BOOLEAN)
}
```

### Colour Scheme

![ ](img/Brandmark%20-%20make%20your%20logo%20in%20minutes%202023-01-11%2016-39-29.jpg)

### Heading and body font

[Quicksand](https://fonts.google.com/specimen/Quicksand?query=Qui#styles)

<!---
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;500&display=swap" rel="stylesheet">

CSS rules to specify families:
font-family: 'Quicksand', sans-serif;

>
