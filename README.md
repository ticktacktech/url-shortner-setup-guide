# URL Shortner Setup Guide

This repository contains the Docker Compose setup to run the URL Shortener project, which includes:
✅ A Node.js backend (Express + PostgreSQL)
✅ A React frontend (TypeScript)
✅ A PostgreSQL database

# Project Structure

url-shortner-/  
  ├── url-shortner-backend/    
  ├── url-shortner-frontend/   
  ├── docker-compose.yml  
  ├── README.md               

# Prerequisites

Before running the project, ensure you have:

✅ Docker installed
✅ Docker Compose installed
✅ Git installed → Download Git

# Setup & Installation

**Clone the Setup Repository**

git clone <this-repo-url> url-shortner-docker
cd url-shortner-docker

**Clone Backend & Frontend Repositories**

git clone https://github.com/ticktacktech/url-shortener-backend.git

git clone https://github.com/ticktacktech/url-shortener-frontend.git

docker-compose up --build or sudo docker-compose up

# PostgreSQL Database Setup

**Access PostgreSQL CLI**

docker exec -it postgres-container psql -U postgres

**Create Database**

CREATE DATABASE url_shortner_database;

**Verify the database**

\l

#  Environment Variables Setup
 
Create a .env file inside url-shortner-backend/ and add the following:

DATABASE_URL="postgresql://postgres:postgres@db:5432/url_shortner_database"


#  API Endpoints


Method	Endpoint	Description
POST	/shorten	Shorten a long URL
GET	/:shortUrl	Redirect to original URL

**Example POST request:**

{
  "longUrl": "https://example.com"
}

**Example Response:**

{
  "shortUrl": "abc123"
}


#  Troubleshooting

**Permission Denied for Docker**

sudo chmod 666 /var/run/docker.sock

**Container Not Starting**

docker-compose down  
docker-compose up --build

**Stopping & Cleaning Up**

docker-compose down
docker system prune -a

**To remove all Docker images, volumes, and networks:**

docker system prune -a
