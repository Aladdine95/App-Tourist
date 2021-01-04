# Tourist App

A Pokémon Go–style Android app for exploring real places across France — monuments, museums, churches, castles, stadiums. Built for the "Developing Application" course at CY Cergy Paris Université (thanks to Manos Katsomallos for the class), with Quitterie Pilon and Dimitri Romano.

## How it works

Every point of interest is plotted on a Google Map with a marker styled after its category (castle, church, monument, museum, stadium). Walk within 200 meters of one and it gets marked as visited, earning you points toward your score and progression level — the goal being to visit as many places as possible.

A background service (`NearestLocationService`) listens for location updates and continuously figures out which unvisited place is closest to you, firing a notification with its name and distance so you don't have to keep the map open. Tapping the notification jumps straight to that spot on the map.

Accounts (pseudo, password, email, age, profile picture) are stored locally through a small SQLite wrapper (`DBHandler`), and the dashboard's progress bar, score and level refresh live via a background thread that polls the database for changes.

## Project structure

```
app/src/main/java/com/romano/dimitri/touristapp/
├── MainActivity.java            # login screen, routes to Register or Dashboard
├── RegisterActivity.java        # account creation, profile picture upload
├── DashboardActivity.java       # hosts the two dashboard fragments
├── UserFragment.java            # profile panel: picture, score, progression, visited list
├── MapsFragment.java            # the Google Map, markers, geolocation, visit validation
├── NearestLocationService.java  # background service: nearest-place tracking + notifications
├── DBHandler.java               # local SQLite storage for users/places/visits
└── model/
    ├── User.java
    ├── Place.java
    └── Visited.java
```

## Stack

Android (Java), Google Maps SDK, Google Play Services Location, SQLite.

## Status

Course project, built over one semester — functional end-to-end (register, log in, explore the map, earn points) but scoped to what could realistically ship in a semester, not maintained since.
