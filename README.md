# Project 2: Image Processing Micro Service on AWS

# Image Filtering API

A simple RESTful API built with Node.js and Express that downloads an image from a public URL, applies basic filters (resize, greyscale, quality adjustment), and returns the filtered image.

This project is part of the **Udacity Full-Stack Cloud Developer Nanodegree**.

---

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoint](#api-endpoint)
- [Example](#example)
- [Deployment](#deployment)

---

## Features

- Accepts a publicly accessible image URL.
- Resizes the image to 256x256 pixels.
- Converts the image to greyscale.
- Reduces JPEG quality to 60%.
- Deletes temporary files after processing.
- Returns appropriate HTTP status codes (`200`, `400`, `422`). 

## Installation
- Set up node environment.You'll need to create a new node server. 
- Open a new terminal within the project directory and run:
  - Initialize a new project: npm i 
  - run the development server with : npm run dev

## Usage
### Root Endpoint
- *Request:* 
  - GET /
- *Description:*
Returns a simple message guiding the user to the filtered image endpoint.
- *Response Example:*
try GET /filteredimage?image_url={{URL}}

---

## Filtered Image Endpoint
- *Request:*
GET /filteredimage?image_url={{PUBLIC_IMAGE_URL}}

- *Description:*
Downloads the image from the given public URL, applies filters (resize, greyscale, quality adjustment), and returns the processed image.

## API Endpoint

### GET /filteredimage
**Query Parameter**

| Parameter   | Description                       |
|------------|-----------------------------------|
| `image_url` | URL of a publicly accessible image |

**Responses**
- `200 OK` – filtered image returned  
- `400 Bad Request` – missing `image_url` query parameter  
- `422 Unprocessable Entity` – unable to process image

**Response Example:**
The response is the filtered image itself. For example, opening the URL in a browser will show the processed image, or using curl will save it locally.

# Example
- **Curl Example:**
curl "http://localhost:8082/filteredimage?image_url=https://webneel.com/wallpaper/sites/default/files/images/07-2013/6%20lamborghini%20car%20wallpaper.jpg" --output output.jpg

- **Using Browser:**
http://localhost:8082/filteredimage?image_url=https://via.placeholder.com/300.jpg

# Deployment
Deployed on AWS Elastic Beanstalk:
http://my-env.eba-bij2ghb7.us-east-1.elasticbeanstalk.com/filteredimage?image_url=<PUBLIC_IMAGE_URL>

- for example : http://my-env.eba-bij2ghb7.us-east-1.elasticbeanstalk.com/filteredimage?image_url=https://webneel.com/wallpaper/sites/default/files/images/07-2013/6%20lamborghini%20car%20wallpaper.jpg