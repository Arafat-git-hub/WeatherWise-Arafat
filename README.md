# 🌦️ WeatherWise: Intelligent Weather Analysis & Advisory System

## Overview

## 

**WeatherWise** is a Python-based intelligent weather advisor application designed to interpret natural language queries, retrieve current and forecast weather data, and generate tailored, conversational advice.

This project was built following a strict **Modular Pipeline** architecture, emphasizing **robustness** through well-defined data contracts and comprehensive error handling. A key focus of this development was the use of **Intentional Prompting** techniques to guide AI tools (like Gemini/ChatGPT) through the design, debugging, and refinement process.

## 🚀 Key Features

## 

*   **Intelligent Advisory:** Converts complex weather data into simple, actionable advice (e.g., "It's safe to bike, but bring a light jacket as the temperature will drop below by 6 PM").
    
*   **Robust Data Retrieval:** Functions as a unified interface to multiple weather providers, primarily using `fetch-my-weather` with a guaranteed fallback to the **wttr.in** API using explicit JSON formatting (`?format=j1`).
    
*   **Crash-Proof Contract:** The core `get_weather_data` function is engineered to _always_ return a standardized dictionary containing either valid weather data or an explicit `'error'` key, ensuring the application never crashes on API failure or invalid input (a direct result of iterative prompting).
    
*   **Interactive UI:** Utilizes `ipywidgets` to provide a user-friendly, interactive experience directly within the notebook environment (e.g., Google Colab).
    
*   **Data Visualization:** Renders charts (e.g., using `matplotlib` or `altair`) to visualize forecast trends (temperature, precipitation, wind speed) alongside the advisory text.
    

## 🛠️ Project Architecture (Modular Pipeline)

## 

The system is structured as a clear, sequential data pipeline to maximize testability and modularity:

1.  **Input** → **NLU:** Parses the user's question to extract _Location_ and _Intent_.
    
2.  **NLU** → **Data Retrieval:** Calls the robust `get_weather_data` function.
    
3.  **Data Retrieval** → **Response Generation:** Uses the standardized weather data contract to generate the conversational response.
    
4.  **Visualization:** Creates dynamic charts based on the processed forecast data.
    

This approach ensures that each module is independent and only relies on the strictly defined output structure of the previous step.

## 📋 Setup and Installation

## 

This project is designed to run seamlessly in a **Google Colab** environment.

### Prerequisites

## 

You will need the following Python packages installed:

    # Recommended environment setup
    pip install requests fetch-my-weather ipywidgets
    

### Getting Started

## 

1.  **Clone the Repository:**
    
        git clone https://github.com/Arafat-git-hub/WeatherWise-Arafat.git
        cd WeatherWise-Arafat
        
    
2.  **Open the Notebook:** Launch the main application notebook in Google Colab:  
    
3.  **Run Cells:** Execute the cells sequentially. The interactive UI powered by `ipywidgets` will appear, allowing you to input natural language weather questions.
    

## 🧠 Intentional Prompting Log

## 

A critical component of this project is demonstrating a sophisticated, collaborative approach to development using AI.

*   **`PROMPTING.md`:** Contains the detailed, documented "Before/After" examples showing how specific, targeted prompts were used to solve architectural flaws (like returning `None` instead of an error dict), fix data inconsistencies (like calculating total precipitation from hourly data), and implement helper functions (`safe_get`, `to_title`).
    
*   **`CONVERSATION_LOG.txt`:** Provides the raw, formatted transcripts of the development conversation, including the initial architectural strategy discussion.
