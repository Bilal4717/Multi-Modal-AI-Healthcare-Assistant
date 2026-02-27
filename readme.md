Diagnosify: Multi-Modal AI Healthcare Assistant
Diagnosify is an intelligent hospital management ecosystem that combines a robust Flask-based backend with AI-driven automation. It features an advanced chatbot for appointment scheduling and medical inquiries, alongside Computer Vision modules for safety compliance and biometric identification.

🚀 Key Features
1. Intelligent AI Chatbot (LangGraph + RAG)
Intent Recognition: Automatically classifies user queries into scheduling, doctor recommendations, or general medical knowledge.

Structured Appointment Scheduling: Uses GPT-4o to extract Patient/Doctor IDs, dates, and times from natural language to book appointments directly into the PostgreSQL database.

RAG (Retrieval-Augmented Generation): Utilizes a FAISS vector store and LangChain to answer specific hospital-related questions based on a diagnosify_data.pdf knowledge base.

Doctor Matchmaker: Recommends the best-suited doctor based on user-described symptoms.

2. Computer Vision Suite
Mask Compliance Detection: A real-time YOLOv8 implementation using the supervision library to detect if patients/staff are wearing masks.

Face Recognition & Registration: A biometric system powered by DeepFace (SFace) and FAISS for registering and recognizing users via cosine similarity.

3. Hospital Management System (HMS)
Full CRUD Operations: Manage Patients, Doctors, Appointments, and Medical Records.

Automated Billing: Logic to calculate total expenses based on doctor fees, pharmacy purchases, and lab test prices.

Departmental Modules: Includes dedicated interfaces for Pharmacy, Lab Tests, and Patient Records.

🛠️ Tech Stack
Backend: Flask, SQLAlchemy (PostgreSQL)

AI/LLM: LangChain, LangGraph, OpenAI GPT-4o

Vector Search: FAISS

Computer Vision: YOLOv8, DeepFace, OpenCV, Supervision

Database: PostgreSQL

📋 Prerequisites
Before running the application, ensure you have the following installed:

Python 3.9+

PostgreSQL

OpenAI API Key (for the chatbot)

🔧 Installation & Setup
Clone the Repository:

Bash
git clone https://github.com/your-username/diagnosify.git
cd diagnosify
Install Dependencies:

Bash
pip install -r requirements.txt
Environment Variables:
Create a .env file in the root directory and add your keys:

Code snippet
OPENAI_API_KEY=your_openai_api_key_here
Database Configuration:
Ensure your PostgreSQL server is running and update the URI in the code:

Python
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql+psycopg2://username:password@localhost:5432/Hospital_Management_System'
Prepare Data:

Place your knowledge base PDF as diagnosify_data.pdf.

Ensure your YOLO weights are saved as mask.pt.

Run the Application:

Bash
python app.py
🏗️ System Architecture
The system follows a modular architecture where the LangGraph workflow acts as the brain, routing requests between the database (via SQLAlchemy) and the vector store (via FAISS). The Flask routes serve both as a REST API for the frontend and a controller for the real-time video streaming threads.