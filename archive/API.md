# Net+ Showdown API Documentation

## Overview
Structured REST API for front-end interaction with Google Sheets database via Apps Script.

Base URL: https://script.google.com/macros/s/YOUR_DEPLOYMENT_ID/exec

## Authentication
All requests include X-API-Key header (configured in Apps Script Properties)

## Endpoints

### GET /state
Returns current game state
Response: { status, currentId, startTime, questionEndTime }

### POST /game
Actions: start, next, end, reset
Body: { action, questionId?, apiKey }

### POST /answer
Submit player answer
Body: { player, questionId, answer, correct, points, time, apiKey }

### GET /questions
Returns all questions (cached)
Response: [{id, question, options, correct, category, explanation}]

### GET /leaderboard
Returns top 10 players
Response: [{player, totalPoints, correctCount}]

## Error Handling
All responses: { success: boolean, data?: any, error?: string }
HTTP status codes: 200, 400, 401, 500
