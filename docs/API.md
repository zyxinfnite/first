# API Documentation

## Base URL

```
http://localhost:5000/api
```

## Authentication

All protected endpoints require a JWT token in the Authorization header:

```
Authorization: Bearer <your_jwt_token>
```

## Endpoints

### Projects

#### List Projects

- **URL**: `/projects`
- **Method**: `GET`
- **Auth**: Required
- **Response**: 
  ```json
  [
    {
      "id": "uuid",
      "name": "My Project",
      "description": "A coding project",
      "language": "python",
      "createdAt": "2024-01-01T00:00:00Z",
      "updatedAt": "2024-01-01T00:00:00Z"
    }
  ]
  ```

#### Create Project

- **URL**: `/projects`
- **Method**: `POST`
- **Auth**: Required
- **Body**:
  ```json
  {
    "name": "My Project",
    "description": "A coding project",
    "language": "python",
    "osType": "linux"
  }
  ```

#### Get Project

- **URL**: `/projects/:id`
- **Method**: `GET`
- **Auth**: Required

#### Update Project

- **URL**: `/projects/:id`
- **Method**: `PUT`
- **Auth**: Required

#### Delete Project

- **URL**: `/projects/:id`
- **Method**: `DELETE`
- **Auth**: Required

### Code Execution

#### Execute Code

- **URL**: `/projects/:id/execute`
- **Method**: `POST`
- **Auth**: Required
- **Body**:
  ```json
  {
    "code": "print('Hello, World!')",
    "language": "python"
  }
  ```
- **Response**:
  ```json
  {
    "output": "Hello, World!",
    "error": null,
    "executionTime": 1500
  }
  ```

### AI Assistance

#### Get Code Suggestions

- **URL**: `/assist`
- **Method**: `POST`
- **Auth**: Required
- **Body**:
  ```json
  {
    "code": "def hello",
    "language": "python",
    "type": "completion"
  }
  ```
- **Response**:
  ```json
  {
    "suggestions": [
      "def hello():",
      "def hello(name):"
    ]
  }
  ```

#### Debug Code

- **URL**: `/assist/debug`
- **Method**: `POST`
- **Auth**: Required
- **Body**:
  ```json
  {
    "code": "x = 1 / 0",
    "error": "ZeroDivisionError: division by zero",
    "language": "python"
  }
  ```
- **Response**:
  ```json
  {
    "explanation": "You're dividing by zero...",
    "fix": "Check if denominator is not zero before division"
  }
  ```

#### Get Learning Resources

- **URL**: `/assist/learn/:topic`
- **Method**: `GET`
- **Auth**: Required
- **Response**:
  ```json
  {
    "topic": "loops",
    "explanation": "...",
    "examples": ["..."],
    "exercises": ["..."]
  }
  ```

### Notifications (Mobile)

#### Register Device Token

- **URL**: `/notifications/register`
- **Method**: `POST`
- **Auth**: Required
- **Body**:
  ```json
  {
    "token": "expo_push_token",
    "platform": "ios|android",
    "device": "physical|simulator"
  }
  ```

#### Subscribe to Topics

- **URL**: `/notifications/subscribe/:topic`
- **Method**: `POST`
- **Auth**: Required
- **Topics**: `code-assistance`, `project-updates`, `collaboration`

## WebSocket Events

### Connect

```javascript
const ws = new WebSocket('ws://localhost:5000/ws');
```

### Messages

#### Execute Code Stream

```json
{
  "type": "execute",
  "projectId": "uuid",
  "code": "print('streaming output')",
  "language": "python"
}
```

#### Response Stream

```json
{
  "type": "output",
  "data": "streaming output",
  "timestamp": "2024-01-01T00:00:00Z"
}
```

#### AI Real-time Assistance

```json
{
  "type": "assist",
  "code": "def ",
  "language": "python"
}
```

## Error Responses

```json
{
  "error": "Error message",
  "code": "ERROR_CODE",
  "timestamp": "2024-01-01T00:00:00Z"
}
```

Common Error Codes:
- `UNAUTHORIZED` - Missing or invalid authentication
- `NOT_FOUND` - Resource not found
- `INVALID_REQUEST` - Invalid request body
- `EXECUTION_ERROR` - Error during code execution
- `RATE_LIMITED` - Too many requests

## Rate Limiting

- **Default**: 100 requests per minute per user
- **Headers**:
  - `X-RateLimit-Limit`
  - `X-RateLimit-Remaining`
  - `X-RateLimit-Reset`