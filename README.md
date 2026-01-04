# ETL of Duolingo data from (unofficial) REST endpoints
The project provides a script for extracting data from Duolingo’s unofficial endpoints and loading it into an SQL database.

The main goal of the script is to retrieve learning progress and activity metrics (as exposed by Duolingo’s web/mobile backend) and load them into a SQL database for further exploration and analysis.

The ETL processes data for a given Duolingo username (or user id), enabling analysis of learning behavior over time (XP trends, streaks, course progress, etc.).

## Key information processed:

user profile basics (name, avatar, current language/course)

streak metrics (current streak, longest streak, streak freeze, etc. if available)

XP metrics (total XP, daily XP where available, league info)

course / unit / skill progress (completed skills/units, crowns/levels where available)

recent activity summaries (last practice timestamp / activity feed if available)

# Project overview

The project contains four modules:

## extraction

### Provides objects for authentication (if needed) and retrieving data.

### Handles session management, headers, cookies, and rate limiting.

### Fetches raw JSON from Duolingo endpoints.

## transformation

### Provides an object for cleaning and normalizing Duolingo JSON into relational tables.

### Ensures consistent types, timestamps, and de-duplication.

## load

### Stores a sqlite database file (or supports Postgres/MySQL if you extend it).

### Provides an object that creates tables and loads data using inserts/upserts.

## main.py

Aggregates the project flow and runs the ETL end-to-end.
