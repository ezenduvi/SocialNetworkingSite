# SocialNetworkingSite
# Multi-threaded API Web Server and Distributed 2PC Database

This project is a multi-threaded web server with a distributed database that implements a Two-Phase Commit (2PC) protocol. The web server hosts a dynamic Single Page Application (SPA) where users can post their thoughts, and these posts are managed by the 2PC distributed database to ensure strong consistency.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Bonus Implementation](#bonus-implementation)
- [License](#license)

## Project Overview

### Part 1: API Web Server

The API web server serves a dynamic web page that allows users to post their thoughts (referred to as "tweets"). The front-end is built as a Single Page Application (SPA) using JavaScript's `XMLHttpRequest` for asynchronous API calls, ensuring the page does not refresh during interactions.

### Part 2: Distributed 2PC Database

All tweets are stored in a distributed database that uses a Two-Phase Commit (2PC) protocol to ensure data consistency across multiple nodes. The 2PC coordinator balances the load between worker nodes, which handle data storage and locking mechanisms.

## Features

- **Multi-threaded Web Server**: Handles multiple requests concurrently.
- **Dynamic Content**: SPA with real-time updates using JavaScript's `XMLHttpRequest`.
- **User Login**: Simple name-based login with cookie-based session management.
- **2PC Database**: Ensures strong consistency for all tweet data with load balancing and error handling.
- **In-memory Database**: Fast and efficient data storage for tweets.
- **Scalable Architecture**: The database system is designed to handle concurrent data modifications.

## Tech Stack

- **Programming Language**: Python
- **Libraries**:
  - `socket`
  - `select`
  - `threading`
  - `argparse`
  - `json`
  - `uuid`
  - `pytz`
  - `random`
- **Frontend**: HTML, JavaScript (XMLHttpRequest)

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/multi-threaded-api-webserver.git
   cd multi-threaded-api-webserver
2. **Run the worker nodes**:
    python3 worker.py [port]
3. **Run the web server:**:
    python3 coordinator.py [myport] [WorkerHost1:WorkerPort1] [WorkerHost2:WorkerPort2] ...
Usage
1. Access the web server:
Open your web browser and navigate to http://localhost:[webserver_port].

2. Post tweets:
Log in using any username.
Post a tweet via the input field.
View and update existing tweets.
3. Database interactions:
All interactions with tweets (viewing, posting, updating) are handled by the 2PC distributed database, ensuring strong consistency.

API Endpoints
GET /api/tweet: Retrieves all tweets.
POST /api/tweet: Creates a new tweet (requires a JSON body).
PUT /api/tweet/[tweet-id]: Updates an existing tweet by its ID.
POST /api/login: Logs in a user and sets a session cookie.
