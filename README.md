# CrewAI Engineering Team

This project implements a multi-agent "Engineering Team" using [CrewAI](https://www.crewai.com/). The crew is designed to autonomously take high-level software requirements and generate a complete, self-contained application, including:

* A detailed software design document.
* The Python backend code.
* A simple Gradio frontend (UI).
* A suite of unit tests for the backend.

## 🚀 The Team (Agents)

This crew consists of four specialized AI agents that mimic a real-world software team:

* **Engineering Lead:** Receives the high-level requirements and creates a detailed technical design, outlining the necessary classes and methods.
* **Backend Engineer:** Takes the technical design from the Lead and writes the complete, self-contained Python backend module.
* **Frontend Engineer:** Observes the backend code and builds a simple `app.py` using Gradio to demonstrate and interact with the backend.
* **Test Engineer:** Analyzes the backend code and writes a corresponding `test_...py` file with unit tests to ensure code quality and correctness.

## ⚙️ The Workflow (Tasks)

The agents work in a sequential process to build the application:

1.  **Design Task:** The **Engineering Lead** creates a design document (`.md`) based on the input requirements.
2.  **Code Task:** The **Backend Engineer** uses the design document to write the core Python module (e.g., `accounts.py`).
3.  **Frontend Task:** The **Frontend Engineer** uses the completed backend module to create a runnable Gradio UI (`app.py`).
4.  **Test Task:** The **Test Engineer** uses the completed backend module to write the unit tests (e.g., `test_accounts.py`).

All generated files are saved in the `output/` directory.

## 🏁 Getting Started

### Prerequisites

* Python 3.10+
* Access to AI models (e.g., OpenAI, Anthropic). This project is configured to use **GPT-4o** and **Claude 3.7 Sonnet**.

### 1. Clone the Repository

```bash
git clone [https://github.com/your-username/crewai-engineering-team.git](https://github.com/your-username/crewai-engineering-team.git)
cd crewai-engineering-team
````

### 2\. Install Dependencies

Create a `requirements.txt` file with the following content and install it:

**requirements.txt**

```
crewai
crewai-tools
python-dotenv
openai
anthropic
gradio
```

Then, run:

```bash
pip install -r requirements.txt
```

### 3\. Set Up API Keys

Create a `.env` file in the root of the project and add your API keys.

**.env**

```
OPENAI_API_KEY=sk-YourOpenAIKey...
ANTHROPIC_API_KEY=sk-YourAnthropicKey...
```

### 4\. Run the Crew

Execute the main script to start the engineering team:

```bash
python main.py
```

The crew will begin executing the tasks sequentially. You will see the agents' actions printed to the console.

## 📂 Project Structure

```
.
├── config/
│   ├── agents.yaml     # Agent definitions
│   └── tasks.yaml      # Task definitions
├── engineering_team/
│   ├── __init__.py
│   └── crew.py         # CrewBase class definition
├── .env                # Your API keys (secret)
├── main.py             # Main script to run the crew
└── requirements.txt    # Python dependencies
```

## ✨ Customization

To have the crew build a different application, simply modify the variables at the top of `main.py`:

```python
# The high-level requirements for your new application
requirements = """
A new set of requirements for a different tool.
For example, a simple note-taking app that can
save and load notes from a JSON file.
"""

# The name of the main Python file to be generated
module_name = "notes.py"

# The main class name inside that file
class_name = "NoteManager"
```

Run `python main.py` again, and the crew will generate a new set of files in the `output/` directory based on your new requirements.

```