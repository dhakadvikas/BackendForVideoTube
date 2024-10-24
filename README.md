# Backend Video Streaming Project


## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Running the Project](#running-the-project)
- [API Endpoints](#api-endpoints)

## Overview
This project is a backend system for a YouTube-like application that supports user registration, login, and logout functionalities. As development progresses, more features like video uploading, comments, likes, and subscriptions are being added.

## Features
- **User Authentication:**
  - User registration (with email and password)
  - User login (JWT-based)
  - User logout (token invalidation)
  
- **Additional Features in Progress:**
  - Video management (upload, delete, and edit videos)
  - Like/dislike system for videos
  - Comment system
  - Subscription to other users
  - User profile management

## Technologies Used
- **Backend Framework:** Node.js with Express
- **Database:** MongoDB with Mongoose
- **Authentication:** JSON Web Token (JWT)
- **Message Broker (for future features):** RabbitMQ
- **File Storage:** (e.g., cloudinary, local storage, etc.)
- **Containerization:** (for future features) Docker (for RabbitMQ and other services) 



## API Endpoints

### User
| Method | Endpoint                       | Description                                  | Protected |
|--------|--------------------------------|----------------------------------------------|-----------|
| POST   | `/api/v1/user/register`        | Register a new user                          | No        |
| POST   | `/api/v1/user/login`           | Login and get token                          | No        |
| POST   | `/api/v1/user/logout`          | Logout user                                  | Yes       |
| GET    | `/api/v1/user/refresh-token`   | EndPoint to Refresh all Tokens               | Yes       |
| POST   | `/api/v1/user/change-password` | Change password from old to new              | Yes       |
| GET    | `/api/v1/user/current-user`    | Give login user details                      | Yes       |
| PATCH  | `/api/v1/user/update-account`  | Update user fullname and email               | Yes       |
| PATCH  | `/api/v1/user/avatar`          | Change Avatar of the Login user              | Yes       |
| PATCH  | `/api/v1/user/cover-image`     | Change Cover Image of the Login user         | Yes       |
| GET    | `/api/v1/user/c/:username`     | Give channel details like subcribers and all | Yes       |
| GET    | `/api/v1/user/history`         | Give watchHistory of login user              | Yes       |


### Videos
| Method | Endpoint                    | Description                       | Protected |
|--------|-----------------------------|-----------------------------------|-----------|
| POST   | `/api/v1/videos/`           | Upload a video                    | Yes       |
| GET    | `/api/v1/videos/`           | Get videos by search              | Yes       |
| GET    | `/api/v1/videos/:videoId`   | Get a specific video by its ID    | Yes       |
| DELETE | `/api/v1/videos/:videoId`   | Delete a video by its ID          | Yes       |
| PUT    | `/api/v1/videos/:videoId`   | Update video details              | Yes       |

### Comments
| Method | Endpoint                       | Description                       | Protected |
|--------|--------------------------------|-----------------------------------|-----------|
| POST   | `/api/v1/comments/:videoId`    | Post a comment on a video         | Yes       |
| GET    | `/api/v1/comments/:videoId`    | Get comments for a specific video | Yes       |
| DELETE | `/api/v1/comments/c/:commentId`| Delete comments through Id        | Yes       |
| PATCH  | `/api/v1/comments/c/:commentId`| Update comment through Id         | Yes       |

### like
| Method | Endpoint                          | Description                       | Protected |
|--------|-----------------------------------|-----------------------------------|-----------|
| POST   |`/api/v1/likes/toggle/v/:videoId`  | toggle like of video              | Yes       |
| POST   |`/api/v1/likes/toggle/c/:commentId`| toggle like of comment            | Yes       |
| POST   |`/api/v1/likes/toggle/t/:tweetId`  | toggle like of tweet              | Yes       |
| GET    |`/api/v1/likes/videos`             | Get all the Likes of video        | Yes       |

### Tweet(This is similar to community tab)
| Method | Endpoint                          | Description                       | Protected |
|--------|-----------------------------------|-----------------------------------|-----------|
| POST   |`/api/v1/tweets/`                  | Create tweet                      | Yes       |
| GET    |`/api/v1/tweets/user/:userId`      | Get User tweet                    | Yes       |
| PATCH  |`/api/v1/tweets/:tweetId`          | update tweet                      | Yes       |
| DELETE |`/api/v1/tweets/:tweetId`          | delete the Tweet                  | Yes       |

### playlistRouter
| Method | Endpoint                               | Description                       | Protected |
|--------|----------------------------------------|-----------------------------------|-----------|
| POST   |`/api/v1/playlist/`                     | Create Playlist                   | Yes       |
| GET    |`/api/v1/playlist/:playlistId`          | Get Playlist By Id                | Yes       |
| PATCH  |`/api/v1/playlist/:playlistId`          | Update Playlist                   | Yes       |
| DELETE |`/api/v1/playlist/:playlistId`          | delete the Playlist               | Yes       |
| PATCH  |`/api/v1/playlist/add/:videoId/:playlistId`          | Add video to playlist Playlist                   | Yes       |
| PATCH  |`/api/v1/playlist/remove/:videoId/:playlistId`          | Remove video to playlist                   | Yes       |
| GET  |`/api/v1/playlist/user/:userId`          | Get  Playlist of a user                   | Yes       |

### dashboard
| Method | Endpoint                          | Description                       | Protected |
|--------|-----------------------------------|-----------------------------------|-----------|
| GET    |`/api/v1/dashboard/stats`          | Get channel details               | Yes       |
| GET    |`/api/v1/dashboard/videos`         | Get Video upload by channel       | Yes       |

### Subscriptions
| Method | Endpoint                          | Description                       | Protected |
|--------|-----------------------------------|-----------------------------------|-----------|
| POST   |`/api/v1/subscriptions/c/:channelId`| Toggle Subscription to channel                      | Yes       |
| GET    |`/api/v1/subscriptions/c/:channelId`| Got Subsbcriber list of channel | Yes       |
| GET    |`/api/v1/subscriptions/u/:subscriberId` | subscriber list of a User channel                      | Yes       |

### HealthCheck
| Method | Endpoint                          | Description                       | Protected |
|--------|-----------------------------------|-----------------------------------|-----------|
| GET    |`/api/v1/healthcheck`              | Get Health Status                 | Yes       |

