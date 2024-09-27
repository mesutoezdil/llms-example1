# llms-example1

This project demonstrates how to interact with the Prediction Guard API to generate text completions using Go. It includes a program that queries the API to produce a Go code snippet for printing random numbers.

## Table of Contents
- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Environment Variables](#environment-variables)
- [Running the Program](#running-the-program)
- [API Response Example](#api-response-example)
- [Troubleshooting](#troubleshooting)

## Project Overview

The project uses the `predictionguard/go-client` package to interact with the Prediction Guard API. It demonstrates how to set up a client, send a prompt to the API, and print the resulting completion in the terminal.

The prompt sent to the API is as follows:
```
<|im_start|>system
You are a helpful code assistant.<|im_end|>
<|im_start|>user
Write a Go program that prints out random numbers.<|im_end|>
<|im_start|>assistant<|im_end|>
```
The API returns a response containing a Go code snippet that fulfills the prompt.

## Prerequisites

- **Go (Golang)**: Make sure you have Go installed on your system. You can download and install it from [Go's official site](https://golang.org/).
- **Git**: Ensure Git is installed for cloning the repository and version control.
- **Prediction Guard API Key**: You will need an API key from Prediction Guard to authenticate your requests.

## Environment Variables

You must set the `PGKEY` environment variable to your Prediction Guard API key. This key will be used by the client to authenticate requests.

### Setting the Environment Variable

On Linux/macOS:
```bash
export PGKEY="your_actual_api_key"
```

On Windows (Command Prompt):
```cmd
set PGKEY="your_actual_api_key"
```

> **Note**: Replace `"your_actual_api_key"` with the actual API key you obtained from Prediction Guard.

## Running the Program

1. **Clone the Repository**:  
   Clone this repository to your local machine using Git:
   ```bash
   git clone https://gitlab.com/yourusername/llms-example1.git
   cd llms-example1
   ```

2. **Install Dependencies**:  
   Use `go get` to install the required packages:
   ```bash
   go get github.com/predictionguard/go-client
   ```

3. **Run the Program**:  
   Execute the Go program:
   ```bash
   go run main.go
   ```

   Upon running, the program will use the API key provided in the environment variable `PGKEY` to make a POST request to the Prediction Guard API.

## API Response Example

A successful response from the API will generate a Go code snippet similar to the following:

```go
package main

import (
        "fmt"
        "math/rand"
        "time"
)

func main() {
        rand.Seed(time.Now().UnixNano())
        for i := 0; i < 10; i++ {
                fmt.Println(rand.Intn(100))
        }
}
```

### Explanation
- The code snippet prints out 10 random numbers between `0` and `99`.
- The `math/rand` package is used to generate random numbers.
- The random number generator is seeded using the current Unix timestamp (`time.Now().UnixNano()`), ensuring the numbers differ each time the program runs.

## Troubleshooting

1. **401 Authorization Required**:  
   If you receive a `401` status error, ensure that your `PGKEY` environment variable is correctly set with a valid API key.

2. **API Endpoint Unreachable**:  
   Verify that you have an active internet connection and that the API endpoint (`https://api.predictionguard.com`) is not blocked by any firewalls or network restrictions.

3. **Invalid API Key**:  
   Double-check that your API key is valid and has the necessary permissions for using the `completions` endpoint.