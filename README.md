# FastAPI External API Integration

## Description
This project demonstrates how to interact with an external API using Python and FastAPI. The key objectives include:
1. Understanding how to retrieve values from an API.
2. Manipulating API data using Python.
3. Creating a FastAPI service that integrates multiple APIs.
4. Returning structured JSON responses from Python.

## Features
- Fetch posts and comments from an external API (`jsonplaceholder.typicode.com`).
- Retrieve and format posts for a specific user.
- Retrieve and format comments for a specific post.
- Provide a detailed post view, including comments.

## Installation

### Prerequisites
- Python 3.7+

### Setup
1. Clone the repository:
   ```sh
   git clone <repository_url>
   cd <repository_name>
   ```
2. Create a virtual environment (optional but recommended):
   ```sh
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```
3. Install dependencies:
   ```sh
   pip install fastapi uvicorn requests
   ```

## Usage

### Running the API
Start the FastAPI application with Uvicorn:
```sh
uvicorn main:app --reload
```

### API Endpoints

#### Get Posts
**Request:**
```
GET /posts/
GET /posts/?postId={postId}
```
**Response:**
```json
[
    {
        "userId": 1,
        "id": 1,
        "title": "Post Title",
        "body": "Post Body"
    }
]
```

#### Get Comments
**Request:**
```
GET /comments/
GET /comments/?postId={postId}
```
**Response:**
```json
[
    {
        "postId": 1,
        "id": 1,
        "name": "Commenter Name",
        "email": "email@example.com",
        "body": "Comment Body"
    }
]
```

#### Get Formatted Posts by User ID
**Request:**
```
GET /formatted_posts/{userID}
```
**Response:**
```json
{
    "userID": 1,
    "posts": [
        {
            "post_title": "Post Title",
            "post_body": "Post Body"
        }
    ]
}
```

#### Get Formatted Comments by Post ID
**Request:**
```
GET /formatted_comment/{postID}
```
**Response:**
```json
{
    "post_id": 1,
    "comments": [
        {
            "commenter_email": "email@example.com",
            "commenter_name": "Commenter Name",
            "comment": "Comment Body"
        }
    ]
}
```

#### Get Detailed Post with Comments
**Request:**
```
GET /detailed_post/{userID}
```
**Response:**
```json
{
    "userID": 1,
    "posts": [
        {
            "post_id": 1,
            "post_title": "Post Title",
            "post_body": "Post Body",
            "comments": [
                {
                    "commenter_email": "email@example.com",
                    "commenter_name": "Commenter Name",
                    "comment_body": "Comment Body"
                }
            ]
        }
    ]
}
```

## License
This project is licensed under the MIT License.

