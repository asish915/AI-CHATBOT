# 🤖 AI-Powered FAQ Chatbot

A smart, interactive FAQ chatbot that uses Natural Language Processing (NLP) to understand user queries and deliver relevant answers. Instead of relying on rigid keyword matching, this bot uses **semantic similarity** to match user input with the most relevant FAQ answers.

## ✨ Features

* **🧠 Semantic Search:** Uses Hugging Face's `sentence-transformers` (`all-MiniLM-L6-v2`) to convert text into embeddings and find the best match using cosine similarity.
* **📋 Interactive Menu:** Users can type natural language queries or simply select a topic by its number from an automatically generated menu.
* **🗄️ SQLite Logging:** Automatically logs every interaction (session ID, user message, bot response, confidence score, and timestamp) to a local SQLite database (`faq_chatbot_logs.db`) for future analysis and debugging.
* **👋 Greeting & Exit Handling:** Built-in logic to gracefully handle common greetings and exit commands.
* **🔄 Session Tracking:** Generates a unique UUID for every chat session to keep track of user flows.
* **📓 Notebook Ready:** Utilizes `IPython.display` to gracefully handle keyboard interrupts and clear outputs, making it perfect for Jupyter Notebooks or Google Colab.

## 🛠️ Tech Stack

* **Python 3**
* **[Sentence-Transformers](https://sbert.net/):** For generating state-of-the-art text embeddings.
* **SQLite3:** Built-in Python library for lightweight database logging.

## 🚀 Getting Started

### Prerequisites

You will need Python installed on your machine. Install the required dependencies using `pip`:

```bash
pip install sentence-transformers ipython
```

### Running the Chatbot

1. Clone this repository or download the Python script.
2. Run the script in your terminal or a Jupyter Notebook environment.

```bash
python chatbot.py
```

**Note:** The first time you run the script, it will take a few seconds to download the `all-MiniLM-L6-v2` model from Hugging Face.

## ⚙️ Customizing the Knowledge Base

You can easily swap out the default e-commerce FAQs with your own data. Just locate the `FAQ_DATA` list in the script and update the dictionaries:

```python
FAQ_DATA = [
    {
        "topic": "Your Topic Name", 
        "question": "The ideal question format?", 
        "answer": "The answer your bot will provide."
    },
    # Add as many as you need!
]
```

The chatbot will automatically recalculate the embeddings and update the terminal menu based on your new entries.

## 📊 Viewing the Logs

Every time a user interacts with the bot, the system logs the conversation. You can view these logs by querying the local database:

```bash
sqlite3 faq_chatbot_logs.db "SELECT * FROM interaction_logs;"
```

Or use any GUI SQLite viewer like [DB Browser for SQLite](https://sqlitebrowser.org/).

## 🎛️ Tweaking the AI Confidence

If the bot is returning answers for completely unrelated questions, you can increase the `CONFIDENCE_THRESHOLD`. If it's failing to answer valid questions, you can lower it.

```python
# Default is 0.40
CONFIDENCE_THRESHOLD = 0.50 
```

## 👤 Author

**Asish** - [GitHub Profile](https://github.com/asish915)

## 📜 License

This project is open-source and available under the MIT License. Feel free to fork, modify, and use it in your own projects!
