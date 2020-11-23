This is a simple Chatbot written in Python 3.5 with a MySQL database backend. The code builds on my other SimpleBot demo (https://github.com/edbullen/SimpleBot) and introduces some NLP with Python NLTK and basic Machine Learning capabilities to demonstrate Sentence Classification using the NLTK and scikit-learn. The Stanford CoreNLP package, written in Java, is also used to parse grammar and extract sentence topics, subject, object etc.

The ChatBot conversation operates in 3 modes

Chat (just learned responses from previous exchanges)
Statement (receive a statement of fact and store it away)
Question (receive a question and attempt to answer it based on previously stored statements)
As it currently stands (May 2017), the functionality is far from perfect, but it demonstrates the concepts of Natural Language Processing, Sentence Classification and a very basic level of Natural Language Grammar processing.

This version is still at a basic experimentation level - there is no concept of authentication, security etc.

Python Library Dependencies
pymysql

nltk

numpy

pandas

scipy

scikit-learn

Stanford CoreNLP Parser This is a Java package that needs to be download and located in suitable dir for future ref

Java - tested with Java 8, java version "1.8.0_131"

Files and Components
Core Functionality

chatbot.py - main ChatBot library
utils.py - generic function utilities used by ChatBot (config, DB conn etc)
features.py - library for extracting features from sentences using NLTK
botserver.py - Multi-Threaded server to allow multiple clients to connect to the ChatBot via network sockets
simpleclient.py - Simple network sockets client to connect to botserver
Default botserver.py logging location is

./log/bostserver.log
Setup and Test

./config/config.ini - template config file, requires editing before starting the chatbot for the first time.
pwdutil.py - store an encoded password for connecting to the database schema.
setupDatabase.py - drop and recreate the database tables (existing data gets lost).
pingDB.py - test the database configuration: create test table, insert data, query it, drop the test table.
mlClassGenerateRfModel.py - generate a scikit-learn Random Forest Model for sentence classification based on input CSV. Default output file-name is "RFmodel.ml"
Tools and Utilities

All Dump and Load utilities use the ./dump subdirectory by default.

dataDump.py - Dump out a database table in CSV format
dataLoad.py - Load a database table in CSV format
featuresDump.py - read in a CSV of sentences, dump out features using features.py into a CSV
testClassifyModel.py - test the Sentence Classification logic and Model for a given sentence (using the pre-built Random Forest RFmodel.ml model)
testGetAnswer.py - test retreiving an Answer from the chatbot for given sentence
testGetGrammar.py - extract grammar structure for given sentence (using Stanford CoreNLP package)
testStoreStatement.py - parse and store a given Statement sentence in the database.
Install and Setup
Details of installing dependancies for the NLPBot to function are documented in the python_server_config.md note in this repo.

In summary, for a new install, the following steps are required:

Install Python 3.5
