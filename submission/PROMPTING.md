## Prompting Strategies Report

This document reflects on the strategic use of **AI prompting** during the development of the **WeatherWise** Notebook. Prompts were used intentionally to guide the project's architecture, enforce code robustness, debug obscure API quirks, and ensure a high standard of modular design.

## 1. Concept Exploration and Architectural Design

**Purpose:** Used to establish a clear architectural roadmap and clarify ambiguous assignment requirements _before_ development began.

*   **Example Prompt (Architectural):** _“What architectural options should I consider for modularity and robustness, and what are the pros/cons of a state-based versus pipeline approach?”_
    
*   **AI Contribution:** The AI outlined three approaches: **Modular Pipeline**, Conversational State Management, and Data-First Visualization. I selected the **Modular Pipeline**, which enforced clear data contracts and separation of concerns—a critical decision for meeting the robustness criteria.
    
*   **Example Prompt (Requirements):** _“Can you explain the role of `fetch-my-weather`, `ipywidgets`, and the `main()` function in my notebook?”_
    
*   **AI Contribution:** The AI clarified the primary data source (`fetch-my-weather`), the required fallback (`wttr.in`), and that `main()` served purely as a test harness, freeing me to focus on the `ipywidgets` UI.
    

**Reflection:** This phase transformed vague requirements into a **justified, actionable design plan**, ensuring the foundation of the project was robust and correctly structured.

## 2. Implementation and Code Quality Prompts

**Purpose:** Applied to generate clean, modular code for core features and helper utilities, ensuring adherence to Python best practices (e.g., type hinting, defensive programming).

*   **Example Prompt:** _“My parsing code is full of defensive checks. What is the function of the helpers `safe_get` and `to_title`, and how does implementing them improve the modular design of `get_weather_data`?”_
    
*   **AI Contribution:** The AI defined the role of **`safe_get`** (to abstract complex, multi-level dictionary lookups) and **`to_title`** (to standardize string outputs). This guidance directly led to the implementation of cleaner, more readable data processing logic, improving the **modularity** and **testability** of the entire system.
    

## 3. Debugging and Robustness Prompts

**Purpose:** Used to diagnose crashes, resolve functional errors, and enforce the data contract to prevent application failure.

| Challenge | Prompting Goal & AI Contribution | Outcome & Learning Point |
| --- | --- | --- |
| Crash on Bad Input (NoneType error from gibberish location) | Goal: Enforce the contract to always return a dictionary, even on failure. AI Contribution: Suggested returning {'error': '...'} from get_weather_data instead of None, and showed the required isinstance(weather, dict) check in the UI callback. | Achieved crash-proof robustness. User-friendly error messages replaced hard crashes, satisfying a core technical requirement. |
| Inaccurate Data (Precipitation always shows 0.0 mm) | Goal: Resolve the discrepancy between expected and actual data output. AI Contribution: Explained that the daily precipMM field from wttr.in is unreliable and provided the logic to correctly sum the hourly precipitation values instead. | Data accuracy was achieved by addressing an API-specific data inconsistency, turning a functional failure into a successful data transformation step. |
| Type Hint Error (NameError: Optional not defined) | Goal: Fix a Python best-practice error. AI Contribution: Correctly diagnosed the missing import and provided the fix: from typing import Optional. | Maintained high code quality and fixed subtle errors related to Python's typing system. |

## Summary

AI prompting was not a shortcut to code completion; it was a **collaborative problem-solving tool** that structured the development process.

*   **Intentional Prompting** built a resilient structure (Modular Pipeline).
    
*   **Iterative Debugging Prompts** enforced the crash-proof contract and corrected data flaws.
    

Overall, the process helped balance clarity, correctness, and creativity, resulting in a system that is not only functional but architecturally sound.