# Project Reflection

## AI Tools Used
For this project I primarily used **ChatGPT** as my AI assistant. The tool played several roles: clarifying the assignment requirements, guiding architectural decisions, debugging runtime errors, and suggesting improvements for data retrieval and visualization. For example, ChatGPT explained the purpose of `fetch-my-weather` versus the `wttr.in` fallback, and highlighted why `ipywidgets` was required for the interactive UI. It also helped me refine error handling in the `get_weather_data` function so that invalid locations produced user-friendly error messages instead of crashes. Finally, ChatGPT showed me how to aggregate hourly precipitation data to avoid the common problem of always displaying “0.0 mm”.

## Prompting Techniques
I made a deliberate effort to use **intentional prompting strategies** instead of asking broad, vague questions. Often, I broke down my problems into smaller parts and asked AI to focus on specific elements, such as:  
- “Give me a consistent `get_weather_data` function regardless of provider”  
- “Explain the role of `safe_get` and `to_title`”  
- “Why does precipitation always show 0.0 mm?”  

I also used **iterative refinement**. For example, when I got a `NoneType` error on invalid input, I first asked for a diagnosis, then followed up with “show me how to make the function always return a dict,” and finally checked how to update my UI callbacks. This layered approach helped me reach robust solutions faster. Another technique was **scenario prompting**: asking “What happens if I enter a nonsense city like brosktl?” to force the AI to think through failure cases.

## What Worked Well?
I’m proud of how I structured the project into modular components. With guidance from AI, I adopted a **Modular Pipeline architecture**, which means each function (data retrieval, parsing, response generation, visualization) has clear responsibilities and standardized inputs/outputs. This made debugging and testing far easier. I’m also proud of how I leveraged AI to strengthen **error handling and resilience**, which often gets overlooked in small projects. Now the notebook doesn’t just work in the happy path — it fails gracefully when data is missing or inputs are invalid.

## What Would You Do Differently?
If I had more time, I would experiment with integrating a **more capable weather API** (such as OpenWeatherMap or WeatherAPI) instead of being limited to three days with wttr.in. I would also consider connecting a lightweight language model (through the `hands-on-ai` logging system) to improve the natural language responses. The current rule-based system works but lacks nuance; an LLM could make the answers sound more natural and conversational.

## Final Thoughts
This project was a valuable learning experience, not just in terms of Python coding and API integration, but also in how to **collaborate effectively with AI tools**. By practicing intentional prompting, I moved beyond copy-paste coding and instead used AI as a development partner. The process improved my technical understanding, especially around error handling, data normalization, and architectural design. More importantly, it showed me how AI can amplify my own problem-solving skills while still requiring me to think critically about design choices.
