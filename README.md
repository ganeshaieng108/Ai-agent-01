# 🤖 AI Agent using Google ADK

A practical implementation of a **single AI Agent** powered by **Google's Agent Development Kit (ADK)**. This project demonstrates how to build and interact with an intelligent agent that can search the web and answer questions.

---

## 📌 Project Overview

This repository contains a hands-on exploration of Google ADK's capabilities in creating responsive AI agents. The project showcases a simple yet powerful agent that leverages Google Search for real-time information retrieval.

**Key Features:**
- ✅ Basic AI agent setup using Google ADK
- ✅ Integration with Google Search tool
- ✅ Real-time information retrieval
- ✅ Error handling and retry mechanisms
- ✅ Debug session management

---

## 🏗️ Architecture

```
┌─────────────────────────────────┐
│    User Query                   │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│  Helpful Assistant Agent        │
│  (powered by Gemini 2.5-Flash)  │
└────────────┬────────────────────┘
             │
             ▼
┌─────────────────────────────────┐
│   Google Search Tool            │
│   (for current information)      │
└─────────────────────────────────┘
```

---

## 📁 Project Structure

```
Ai-agent-01/
│
├── day01a.ipynb              # Main notebook with agent implementation
├── README.md                 # Project documentation (this file)
└── requirements.txt          # Project dependencies (optional)
```

---

## 📖 Notebook Overview

### **day01a.ipynb**

This Jupyter notebook demonstrates a complete workflow for building and testing an AI agent using Google ADK.

#### **Cell Breakdown:**

1. **Setup & Dependencies**
   - Import necessary libraries and modules
   - Install `google-adk` package
   - Configure environment variables

2. **Authentication**
   - Load Google API Key from Kaggle Secrets
   - Initialize secure API access

3. **ADK Components Import**
   - Agent
   - Gemini LLM model
   - InMemoryRunner for agent execution
   - Google Search tool

4. **Helper Functions**
   - `get_adk_proxy_url()`: Generates proxied URL for ADK web UI
   - Handles Kaggle Notebook environment configuration

5. **Retry Configuration**
   - Sets up HTTP retry options for robust API calls
   - Handles rate limiting and server errors gracefully

6. **Agent Definition**
   - Creates a helpful assistant agent
   - Configures Gemini 2.5-Flash model
   - Integrates Google Search tool

7. **Runner Setup**
   - Initializes InMemoryRunner for agent execution
   - Manages agent session state

8. **Query Examples**
   - Question 1: "What is Agent Development Kit from Google? What languages is the SDK available in?"
   - Question 2: "How this ADK push on GitHub?"
   - Question 3: "What is cost of sheep cruise?"

---

## 🚀 Getting Started

### Prerequisites

- **Python 3.12+**
- **Google API Key** (with Gemini API access)
- **Jupyter Notebook or Kaggle Notebook Environment**
- **Google ADK** (version 1.29.0+)

### Installation

1. **Install Dependencies:**
   ```bash
   pip install google-adk
   ```

2. **Set Up API Key:**
   - Get your Google API Key from [Google AI Studio](https://aistudio.google.com)
   - Add it to your environment or Kaggle Secrets as `GOOGLE_API_KEY`

3. **Clone the Repository:**
   ```bash
   git clone https://github.com/ganeshaieng108/Ai-agent-01.git
   cd Ai-agent-01
   ```

4. **Open the Notebook:**
   ```bash
   jupyter notebook day01a.ipynb
   ```

---

## 💻 Key Components

### **Agent Configuration**
```python
Agent(
    name="helpful_assistant",
    model=Gemini(
        model="gemini-2.5-flash-lite",
        retry_options=retry_config
    ),
    description="A simple agent that can answer general questions.",
    instruction="You are a helpful assistant. Use Google Search for current info or if unsure.",
    tools=[google_search]
)
```

### **Retry Options**
- Maximum retry attempts: 5
- Exponential backoff with base 7
- HTTP status codes: 429, 500, 503, 504

### **Runner**
- Uses `InMemoryRunner` for lightweight, session-based execution
- Supports debug mode for interactive testing

---

## 🎯 Usage Examples

### Ask a General Question
```python
response = await runner.run_debug(
    "What is Agent Development Kit from Google? What languages is the SDK available in?"
)
```

### Follow-up Questions
```python
response = await runner.run_debug("how this adk push on github")
```

### Continuous Conversation
The runner maintains session state, allowing for multi-turn conversations within the same session.

---

## 📚 Dependencies

Core packages used in this project:

- **google-adk** (1.29.0+): Agent Development Kit
- **google-genai**: Google Generative AI Python SDK
- **FastAPI**: Web framework for ADK
- **PyYAML**: Configuration management
- **Pydantic**: Data validation
- **Python 3.12+**: Runtime environment

For complete dependency list, see the installation logs in the notebook.

---

## 🔧 Configuration

### Environment Variables
- `GOOGLE_API_KEY`: Your Google API key for Gemini access

### Model Configuration
- **Model**: `gemini-2.5-flash-lite`
- **Temperature**: Default (can be customized)
- **Retry Strategy**: Exponential backoff with max 5 attempts

---

## 📝 Features Demonstrated

✅ **Agent Creation**: Build a custom AI agent with specific instructions  
✅ **Tool Integration**: Connect external tools (Google Search)  
✅ **Error Handling**: Implement retry logic for robust API calls  
✅ **Session Management**: Maintain conversation context  
✅ **Debug Mode**: Interactive testing of agent responses  
✅ **Real-time Information**: Use search for current data  

---

## 🌐 Running the ADK Web UI

The notebook includes setup for the ADK web UI for visual monitoring:

1. Run the cell with `!adk web ...` command
2. Wait for it to show "Running" status
3. Click the generated link to open the web interface
4. Monitor agent execution in real-time

---

## 🔍 Troubleshooting

**Issue**: "No running Jupyter servers found"
- Solution: Ensure you're running in a Jupyter environment

**Issue**: API Key authentication error
- Solution: Verify `GOOGLE_API_KEY` is properly set in environment/secrets

**Issue**: Google Search tool not working
- Solution: Confirm your API key has Search API permissions enabled

---

## 📚 Resources

- [Google ADK Documentation](https://google.dev/adk)
- [Google Generative AI API](https://ai.google.dev)
- [Jupyter Notebook Guide](https://jupyter.org)
- [Kaggle Notebooks Help](https://kaggle.com/notebooks)

---

## 📄 License

This project is open-source and available under the MIT License.

---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report issues
- Submit pull requests
- Suggest improvements
- Add more examples

---

## 📧 Contact

For questions or feedback, please reach out through GitHub issues or contact the project maintainer.

---

**Happy Exploring! 🚀**
