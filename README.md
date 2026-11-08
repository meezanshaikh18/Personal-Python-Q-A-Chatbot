# 🐍 Personal Python Q&A Chatbot

A Python-based question-answering chatbot that allows users to ask Python programming questions in natural language and receive relevant answers from a predefined knowledge base.

The project uses traditional **Natural Language Processing (NLP)** techniques, including text preprocessing, TF-IDF vectorization, and Cosine Similarity, to identify the closest matching question and retrieve its corresponding answer.

The chatbot is available through both a **Streamlit Web Interface** and a **Command-Line Interface (CLI)**.

## ✨ Features

- **Natural Language Input:** Ask Python-related questions using different phrasings.
- **NLP Text Preprocessing:** Lowercasing, tokenization, stopword removal, and lemmatization.
- **TF-IDF Vectorization:** Convert stored questions into numerical representations.
- **Cosine Similarity:** Identify the closest matching question.
- **Confidence Threshold:** Apply a configurable similarity threshold of `0.30`.
- **JSON Knowledge Base:** Store questions and answers in separate topic-based files.
- **Fallback Response:** Handle questions that do not match the available knowledge base.
- **Streamlit Web Interface:** Interactive chatbot with chat history and a clear-chat option.
- **Command-Line Interface:** Run the chatbot directly through the terminal.
- **Debug Mode:** Display matched questions and similarity scores.
- **Automated Testing:** Evaluate question matching using 15 predefined test cases.

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| NLTK | Text preprocessing and lemmatization |
| Scikit-learn | TF-IDF vectorization and cosine similarity |
| Streamlit | Interactive web interface |
| JSON | Knowledge base storage |

## 📚 Knowledge Base

The chatbot automatically loads every `.json` file inside the `data/` directory.

| File | Coverage |
|---|---|
| `knowledge_base.json` | Lists, tuples, and dictionaries |
| `basics.json` | Python fundamentals, conditions, loops, and functions |
| `advanced.json` | Sets, comprehensions, lambda functions, OOP, file handling, modules, and exceptions |
| `strings.json` | String methods and f-strings |
| `general.json` | Greetings, general chatbot interactions, thanks, and farewells |

Each knowledge-base entry contains a category, multiple question variations, and a corresponding answer.

New questions and answers can be added by editing existing JSON files or creating additional JSON files inside the `data/` directory.

## 🧠 How It Works

The chatbot follows a text-based question-matching approach.

1. **Load Knowledge:** Read predefined questions and answers from JSON files.
2. **Text Preprocessing:** Convert text to lowercase, tokenize it, remove punctuation and stopwords, and apply lemmatization.
3. **TF-IDF Vectorization:** Convert stored questions into numerical vectors.
4. **Question Matching:** Transform the user's question and calculate Cosine Similarity against stored questions.
5. **Best Match Selection:** Identify the question with the highest similarity score.
6. **Answer Retrieval:** Return the corresponding answer when the similarity score meets the configured threshold.
7. **Fallback Handling:** Return a predefined response when the similarity score is below the threshold.

**Similarity Threshold:** `0.30`

> **Note:** This is a knowledge-base-driven NLP chatbot, not an LLM-powered chatbot. TF-IDF and Cosine Similarity measure lexical similarity rather than deep semantic understanding or generative reasoning.

## 📁 Project Structure

```text
Personal Python Q&A Chatbot/
│
├── app.py                  # Streamlit web application
├── chatbot.py              # Core chatbot and NLP logic
├── cli.py                  # Command-line interface
├── test_bot.py             # Automated testing script
├── requirements.txt        # Python dependencies
├── .gitignore              # Ignored files and directories
├── README.md               # Project documentation
│
└── data/
    ├── knowledge_base.json # Core Python data structures
    ├── basics.json         # Python fundamentals
    ├── advanced.json      # Advanced Python concepts
    ├── strings.json        # Python string operations
    └── general.json        # General chatbot interactions
```

## ⚙️ Installation (Windows / Conda)

This project runs in an isolated **Python 3.13** Conda environment. Your existing system Python 3.15.2, Anaconda base Python 3.14.6, and Conda 26.7.3 do not need to be uninstalled or modified.

Open **Anaconda Prompt**, navigate to the extracted project directory, and run:

```bat
conda env create -f environment.yml
conda activate python-qa-chatbot
python --version
python -m pip --version
python -m pip install -r requirements.txt
```

The `python --version` command should display Python 3.13.x. The `requirements.txt` dependencies are unchanged; Conda selects the compatible interpreter and installs the project's Python packages using pip.

For subsequent sessions, open Anaconda Prompt and run:

```bat
conda activate python-qa-chatbot
cd "PATH\TO\Personal Python Q&A Chatbot"
```

If you prefer not to use `environment.yml`, create the same environment manually:

```bat
conda create -n python-qa-chatbot python=3.13 pip -y
conda activate python-qa-chatbot
python -m pip install -r requirements.txt
```

**Important:** Run `python --version` after activation. Do not use the global Python 3.15 interpreter to install this project's dependencies. The first launch may download NLTK data if internet access is available.

## ▶️ Running the Chatbot

### Option 1: Streamlit Web Application

Run:

```bash
streamlit run app.py
```

Streamlit will provide a local URL in the terminal. Open it in your browser to interact with the chatbot.

### Option 2: Command-Line Interface

Run:

```bash
python cli.py
```

Enter Python-related questions directly in the terminal.

To exit the chatbot, type:

```text
quit
```

You can also use `exit` or `q`.

## 🧪 Testing

The project includes an automated testing script named `test_bot.py`.

Run:

```bash
python test_bot.py
```

The testing script includes 15 predefined test cases covering:

- Python concepts and definitions.
- Lists and tuples.
- Functions and object-oriented programming.
- String operations.
- File handling and exception handling.
- Greetings and unrelated questions.
- Unknown-question detection.

It also evaluates different similarity thresholds:

`0.1, 0.2, 0.3, 0.4, 0.5, 0.6`

The script prints individual PASS/FAIL results and a threshold comparison.

Run the tests locally to verify the results in your environment.

## ⚙️ Configuration

The confidence threshold is defined in `chatbot.py`:

```python
THRESHOLD = 0.3
```

A higher threshold makes the chatbot more selective and may reject more questions.

A lower threshold may return more answers but can increase incorrect matches.

Adjust the threshold only after reviewing the test results.

## ⚠️ Limitations

- The chatbot can only answer questions represented in its predefined knowledge base.
- TF-IDF matching relies heavily on shared words and may not recognize semantically equivalent questions with different wording.
- A question sharing keywords with an unrelated entry may still receive an incorrect answer.
- Each message is treated as a single question.
- The chatbot retrieves stored answers rather than generating new explanations.
- The current test set is limited and cannot establish real-world accuracy.
- The knowledge base and confidence threshold require ongoing evaluation.

## 🔭 Future Improvements

- Integrate Sentence Transformers for semantic question matching.
- Expand the Python knowledge base with additional programming concepts.
- Implement unanswered-question logging.
- Add support for multiple questions in a single message.
- Introduce conversation context and memory.
- Improve confidence scoring and matching accuracy.
- Explore LLM integration for more flexible conversational responses.

## 🎓 Learning Outcomes

Through this project, I explored and implemented:

- Natural Language Processing fundamentals.
- Text preprocessing and tokenization.
- Stopword removal and lemmatization.
- TF-IDF feature extraction.
- Cosine Similarity and text matching.
- JSON-based knowledge management.
- Building interactive applications using Streamlit.
- Developing and testing a Python-based chatbot.

## 👨‍💻 Author

**Meezan Shaikh**

AI/ML Engineer | Python | Machine Learning | NLP | Generative AI

---

*Developed as a practical Python and NLP learning project to explore text preprocessing, information retrieval, and chatbot development.*
