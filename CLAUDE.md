# Claude Development Environment

This document provides context for AI assistants to understand and work with this repository.

## Project Overview

This project provides a unified interface for interacting with Google Gemini models. It consists of three main components:

1.  **Gemini Balance (`gemini-balance`)**: A Docker-based proxy service that manages and forwards requests to the Google Gemini API. It handles API key management, rate limiting, and provides a standardized endpoint. It's configured via `compose.yml` and a `.env` file.

2.  **Claude Code Router (`claude-code-router`)**: A lightweight router that accepts requests in the Claude API format and translates them for the `gemini-balance` service. This allows tools designed for Claude to work with Gemini models. Its configuration is in `claude-code-router/config.json`.

3.  **Gemini CLI (`gemini-cli`)**: A command-line interface for directly interacting with the `gemini-balance` service for tasks like chat and content generation.

## Key Files

-   `ARCHITECTURE.md`: Describes the overall technical architecture of the `gemini-balance` service.
-   `compose.yml`: Docker Compose file to run the `gemini-balance` service.
-   `.env.example`: Example environment variables for configuring `gemini-balance`.
-   `claude-code-router/README.md`: Instructions for setting up and running the router.
-   `claude-code-router/config.json`: Configuration file for the router, defining providers and routing rules.
-   `gemini-cli/README.md`: Instructions for using the command-line interface.

## Development Workflow

### Running the Services

1.  **Start the core proxy**: The `gemini-balance` service is the foundation. It should be started first, typically using Docker Compose.
    ```bash
    # (Assuming you have a .env file based on .env.example)
    docker-compose up -d
    ```

2.  **Start the router**: The `claude-code-router` connects to the `gemini-balance` service.
    ```bash
    ccr code
    ```

### Common Tasks

-   **Modify routing logic**: Edit `claude-code-router/config.json` and restart the router with `ccr restart`.
-   **Test with CLI**: Use the `gemini-cli` to directly test the `gemini-balance` service.
    ```bash
    cd gemini-cli
    npm start
    ```
-   **Check router logs**:
    ```bash
    tail -f ~/.claude-code-router.log
    ```
