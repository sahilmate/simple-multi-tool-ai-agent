# Multi-Tool AI Agent

This project implements a multi-tool AI agent using the [smolagents](https://huggingface.co/docs/smolagents/en/index) framework by Hugging Face. The agent is capable of performing multiple tasks, such as generating jokes, fetching the current time in a specific timezone, and generating images using integrated tools.

## Features

- **Random Joke Generator**: Fetches a random joke from an online API.
- **Timezone-based Time Fetcher**: Retrieves the current time for a specified timezone.
- **Image Generator**: Generates images using a pre-built tool from the Hugging Face Hub.
- **Gradio Integration**: Provides an interactive user interface for interacting with the agent.

## Folder Structure
```
multi-tool-ai-agent/
├── .gitignore
├── README.md
├── JokeAndImageGenerator_LocalTimeTeller/
│   ├── .env
│   ├── .gitattributes
│   ├── agent.json
│   ├── app.py
│   ├── Gradio_UI.py
│   ├── prompts.yaml
│   ├── README.md
│   ├── requirements.txt
│   ├── __pycache__/
│   │   └── Gradio_UI.cpython-311.pyc
│   ├── .gradio/
│   │   └── certificate.pem
│   └── tools/
│       ├── final_answer.py
│       ├── visit_webpage.py
│       ├── web_search.py
│       └── __pycache__/
│           └── final_answer.cpython-311.pyc
```

## Key Files

- **`app.py`**: The main application file where the agent and its tools are defined and configured.
- **`Gradio_UI.py`**: Contains the Gradio-based user interface for interacting with the agent.
- **`prompts.yaml`**: Stores system prompts for guiding the agent's behavior.
- **`tools/`**: Contains custom tools used by the agent, such as `final_answer.py`, `visit_webpage.py`, and `web_search.py`.
- **`.env`**: Stores environment variables, such as the Hugging Face API token (`HF_TOKEN`).

## Tools

### 1. Random Joke Generator
Defined in `app.py`:
```python
@tool
def get_random_joke() -> str:
    """A tool that fetches a random joke from an online API."""
```

### 2. Timezone-based Time Fetcher
Defined in `app.py`:
```python
@tool
def get_current_time_in_timezone(timezone: str) -> str:
    """Fetches the current time for a given timezone."""
```

### 3. Image Generator
Imported from the Hugging Face Hub:
```python
image_generation_tool = load_tool("agents-course/text-to-image", trust_remote_code=True)
```

## How to Run

### 1. Install Dependencies
Install the required Python packages using `requirements.txt`:
```sh
pip install -r requirements.txt
```

### 2. Set Up Environment Variables
Create a `.env` file in the `JokeAndImageGenerator_LocalTimeTeller/` directory and add your Hugging Face API token:
```
HF_TOKEN=your_huggingface_api_token
```

### 3. Run the Application
Launch the Gradio interface:
```sh
python app.py
```

### 4. Interact with the Agent
Use the Gradio interface to interact with the agent and perform tasks.

## Requirements

- Python 3.11 or higher
- Hugging Face `smolagents` library
- `Gradio` for the user interface

## Example Usage

- **Generate a Joke**: Ask the agent to fetch a random joke.
- **Get Current Time**: Provide a timezone, and the agent will return the current time in that timezone.
- **Generate an Image**: Use the image generation tool to create AI-generated images.

## Notes

- The agent uses the `Qwen/Qwen2.5-Coder-32B-Instruct` model by default. If the model is overloaded, you can switch to another Hugging Face model or endpoint.
- The `.env` file should not be pushed to version control as it contains sensitive information.


## Next Up
# smolagents
### Fine tuning a model for Function Calling 
- https://huggingface.co/agents-course/notebooks/blob/main/bonus-unit1/bonus-unit1.ipynb

### smolagents Party Planner with CodeAgent
- https://huggingface.co/agents-course/notebooks/blob/main/unit2/smolagents/code_agents.ipynb

### smolagents Party Planner with ToolCallingAgent
- https://colab.research.google.com/github/huggingface/agents-course/blob/main/notebooks/unit2/smolagents/tool_calling_agents.ipynb

### Tool Creation methods
- https://colab.research.google.com/github/huggingface/agents-course/blob/main/notebooks/unit2/smolagents/tools.ipynb

### Agentic RAG systems 
- https://colab.research.google.com/github/huggingface/agents-course/blob/main/notebooks/unit2/smolagents/retrieval_agents.ipynb

### Multi Agent Systems
- https://colab.research.google.com/github/huggingface/agents-course/blob/main/notebooks/unit2/smolagents/multiagent_notebook.ipynb

### Vision and Browser Agents
- https://colab.research.google.com/github/huggingface/agents-course/blob/main/notebooks/unit2/smolagents/vision_agents.ipynb

## Acknowledgments

- [Hugging Face smolagents](https://huggingface.co/docs/smolagents/en/index)
- [Gradio](https://gradio.app/)

