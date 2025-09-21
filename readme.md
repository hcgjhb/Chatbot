# **LangGraph & Streamlit: Stateful Chatbot with Persistent Memory**

This project is a full-stack conversational AI chatbot that demonstrates how to build a stateful application with persistent memory. It uses LangGraph for the backend logic, Google Gemini as the language model, and Streamlit for the user interface. All conversations are saved to a SQLite database, allowing users to resume them at any time.

## **✨ Features**

* **Interactive Chat Interface**: A clean and user-friendly web interface built with Streamlit.  
* **Persistent Conversation History**: Every chat is automatically saved to a SQLite database, so you never lose a conversation.  
* **Multi-Session Management**: Users can create new chats or resume any previous conversation from a list in the sidebar.  
* **Real-time Streaming**: AI responses are streamed back to the user token-by-token for a dynamic and engaging user experience.  
* **Powered by Google Gemini**: Leverages the gemini-2.5-flash model for intelligent and fast responses.

## **🏛️ Architecture**

The application is split into two main components:

1. **Backend (langgraph\_database\_backend.py)**:  
   * A StateGraph from LangGraph is defined to manage the conversational state (the list of messages).  
   * It integrates with the Google Gemini API to generate chat responses.  
   * The graph is compiled with a SqliteSaver checkpointer, which automatically saves the state of every conversation thread to a chatbot.db file, providing persistence.  
2. **Frontend (streamlit\_frontend\_database.py)**:  
   * A Streamlit application that serves as the user interface.  
   * It communicates directly with the compiled LangGraph chatbot object from the backend.  
   * It uses unique thread\_ids (UUIDs) to create, manage, and switch between different conversations.  
   * The sidebar lists all past conversations by retrieving the saved thread IDs from the backend.

## **🛠️ Tech Stack**

* **Backend**: LangGraph, LangChain, Google Generative AI (langchain-google-genai)  
* **Frontend**: Streamlit  
* **Database**: SQLite  
* **Language**: Python

## **🚀 Getting Started**

Follow these instructions to set up and run the project locally.

### **1\. Prerequisites**

* Python 3.8+  
* A Google API Key. You can get one from [Google AI Studio](https://aistudio.google.com/app/apikey).

### **2\. Installation & Setup**

1. **Clone the repository:**  
   git clone \<your-repository-url\>  
   cd \<your-repository-name\>

2. **Create a virtual environment and activate it:**  
   \# For macOS/Linux  
   python3 \-m venv venv  
   source venv/bin/activate

   \# For Windows  
   python \-m venv venv  
   .\\venv\\Scripts\\activate

3. Install the required dependencies:  
   Create a file named requirements.txt and add the following lines:  
   streamlit  
   langgraph  
   langchain-core  
   langchain-google-genai  
   python-dotenv

   Then, install them using pip:  
   pip install \-r requirements.txt

4. Set up your environment variables:  
   Create a file named .env in the root of your project directory and add your Google API key:  
   GOOGLE\_API\_KEY="YOUR\_GOOGLE\_API\_KEY\_HERE"

### **3\. Usage**

1. Run the Streamlit application:  
   Open your terminal in the project directory and run the following command:  
   streamlit run streamlit\_frontend\_database.py

2. Open the application:  
   Your web browser should automatically open a new tab with the chatbot interface. If not, navigate to the local URL displayed in your terminal (usually http://localhost:8501).

## **📁 File Structure**

.  
├── langgraph\_database\_backend.py   \# Defines the LangGraph agent and database connection  
├── streamlit\_frontend\_database.py  \# The Streamlit frontend application  
├── requirements.txt                \# Project dependencies  
└── .env                            \# Environment variables for API key

## **📜 License**

This project is licensed under the MIT License.