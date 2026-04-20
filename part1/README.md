Hello, this is techincal documentation for HBNB(part1), :)))

1. Introduction

This project is a basic backend system similar to an Airbnb-style application. It lets users register, create places to stay, leave reviews, and manage amenities.

The system is split into three layers:

API layer: receives requests and sends responses
Business layer: handles rules and logic
Database layer: stores data

We use this structure to keep things organized and avoid mixing logic everywhere (which gets messy fast).

2. High-Level Architecture
What the system looks like
The API receives requests from users
It sends them to the business layer (services)
The business layer handles everything important
The database just stores and returns data
Simple structure idea
API → Service (Facade) → Models → Database
Why this setup

Because if everything talks to everything directly, the project becomes unmaintainable very quickly.

3. Business Logic Layer (Main Classes)

This is where the core data and rules live.

👤 User

A user of the system.

Fields:

id
first name
last name
email
password
is_admin
created_at
updated_at

What it does:

Can register
Can update profile
Can own places
Can write reviews
🏠 Place

A property listed by a user.

Fields:

id
title
description
price
latitude
longitude
owner (user)
created_at
updated_at

What it does:

Created by a user
Can have multiple reviews
Can have multiple amenities
⭐ Review

A comment left by a user about a place.

Fields:

id
rating
comment
created_at
updated_at

What it does:

Linked to one user
Linked to one place
Can be created, edited, deleted
🧾 Amenity

A feature of a place (like WiFi or pool).

Fields:

id
name
description
created_at
updated_at

What it does:

Can be attached to many places
Helps describe what a place offers
Relationships (simple version)
One user can create many places
One user can write many reviews
One place has many reviews
One place has many amenities
4. API Flows (How requests move through the system)
👤 User Registration

What happens when someone signs up:

User sends data to API
API sends it to business logic
Password is hashed
User is saved in database
System returns success
🏠 Create Place

What happens when a user creates a place:

API receives request
User token is checked
System links place to user
Place is saved in database
Confirmation is returned
⭐ Submit Review

What happens when a user leaves a review:

API receives request
User is authenticated
System checks that place exists
Review is saved
Response is sent back
📍 Get List of Places

What happens when someone requests places:

API receives request
Filters are read (if any)
Database is queried
List of places is returned
5. Main Idea of the Design

The whole system is built to keep things separated:

API doesn’t handle logic
Business layer handles rules
Database just stores data

This makes the system easier to maintain and extend later.
