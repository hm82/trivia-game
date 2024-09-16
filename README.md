# Trivia Game

Welcome to the Trivia Game project! This repository contains a simple trivia game application with a React frontend, a Python backend, and AWS services including API Gateway, Lambda Functions, and Step Functions.

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Features](#features)
- [Technologies](#technologies)
- [Setup and Installation](#setup-and-installation)
  - [Frontend](#frontend-react)
  - [Backend](#backend-python)
  - [AWS Services](#aws-services)
- [How to Play](#how-to-play)
- [Future Improvements](#future-improvements)
- [Contributing](#contributing)

## Overview

This is a simple trivia game where players can answer multiple-choice questions. The game flow is managed by AWS Step Functions, while the backend logic for serving questions and evaluating answers is handled by AWS Lambda functions. The frontend is built with React and fetches data from the backend using AWS API Gateway.

## Architecture

The game follows a serverless architecture utilizing the following AWS services:
- **API Gateway**: Acts as the interface between the React frontend and the backend services.
- **AWS Lambda**: Hosts the backend logic written in Python, responsible for serving questions and evaluating answers.
- **AWS Step Functions**: Orchestrates the flow of the trivia game, including handling game state, scoring, and moving through rounds.

## Features

- Multiple-choice trivia questions.
- Real-time scoring.
- Serverless backend using AWS Lambda and Step Functions.
- Simple and responsive React frontend.
- Data stored and managed using AWS services.

## Technologies

- **Frontend**: React, Tailwind CSS
- **Backend**: Python, AWS Lambda, AWS Step Functions
- **API Gateway**: AWS API Gateway for HTTP routing.
- **AWS Services**: API Gateway, Lambda, Step Functions, S3 (for static hosting).

## Setup and Installation

### Prerequisites

Make sure you have the following installed on your local machine:

- Node.js and npm (for React frontend)
- Python 3.x (for backend development)
- AWS CLI (for deploying AWS services)
- AWS SAM CLI (for building and deploying the serverless application)

### Frontend (React)

1. Clone the repository:

    ```bash
    git clone https://github.com/your-username/trivia-game.git
    cd trivia-game/frontend
    ```

2. Install the dependencies:

    ```bash
    npm install
    ```

3. Configure the API endpoint for the backend in `src/config.js`:

    ```javascript
    export const API_BASE_URL = 'https://<api-gateway-url>';
    ```

4. Start the development server:

    ```bash
    npm start
    ```

5. The frontend should now be running on [http://localhost:3000](http://localhost:3000).

### Backend (Python)

1. Navigate to the backend directory:

    ```bash
    cd ../backend
    ```

2. Install the Python dependencies:

    ```bash
    pip install -r requirements.txt
    ```

3. Create the Lambda functions for:
    - **Fetching questions** from a trivia question pool.
    - **Evaluating answers** and updating game state.

4. Use AWS SAM to deploy the backend:

    ```bash
    sam build
    sam deploy --guided
    ```

5. After deployment, note the API Gateway URL that SAM provides. This URL will be used by the React frontend to interact with the backend.

### AWS Services

#### API Gateway

- The API Gateway routes HTTP requests to the Lambda functions.
- Ensure your API Gateway routes are correctly set up to forward requests to the Lambda backend.

#### Lambda Functions

- Create Lambda functions in Python for the following:
  - **GetQuestions**: Fetches a set of trivia questions from a pre-defined pool.
  - **SubmitAnswer**: Evaluates the submitted answer and returns feedback.

#### Step Functions

- AWS Step Functions manage the game flow:
  - Handles starting the game, tracking state, and ensuring the player moves through each trivia round.

## How to Play

1. Open the React frontend in your browser.
2. Click "Start Game" to begin.
3. Answer multiple-choice questions.
4. After each round, you'll receive feedback on your answer and your score will be updated in real-time.
5. Continue until all rounds are completed.

## Future Improvements

- Add authentication to allow players to save their scores.
- Introduce categories and difficulty levels for trivia questions.
- Enhance the UI/UX with animations and sound effects.
- Integrate a global leaderboard using DynamoDB.

## Contributing

Contributions are welcome! Feel free to submit a pull request or open an issue if you have any ideas for improvements or bugs to report.

---

Happy gaming! 🎮
