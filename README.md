# Introduction

## Description

**OntoQuest** is a *vocabulary management game* tailored to address the nuanced terminologies and vocabulary within **Infineon Technologies**. With diverse coverage across *Automotive*, *Green Industrial Power*, *Power & Sensor Systems*, and *Connected Secure Systems*, understanding the comprehensive vocabulary becomes a challenge. The game ensures domain-specific vocabulary definitions and terminology standardization, mitigating misunderstandings stemming from multiple meanings of the same words and discrepancies in cross-departmental communication.

## Process
The game's process begins with **domain or department selection**, followed by **ontology selection** and **question quantity**. Users engage in validating vocabulary *definitions*, presenting terms and their definitions, with options to **agree**, **disagree**, or express uncertainty. The completed definitions and *contribution scores* are summarized. The scoring system weighs agreement based on **previous agreements** and **community consensus**, while **disagreement** scoring accounts for *semantic differences*. The stability system utilizes *semantic similarity calculations*, dynamic stability thresholds based on **total reviews**, and **clustering** to consolidate definitions, ensuring coherence and consistency.

# Files Structure

- VOCAB GAME
    - .idea  *(IDE-specific directory for project settings and configurations)*
    - __pycache__
    - FLASK
        - instance  *(Flask instance folder for configuration files)*
        - website
            - static  *(Contains static assets such as CSS, JSON, images, and ontologies)*
                - css
                - json
                - ontologies  *(Stores the ontologies of the game)*
                - picture
            - templates  *(Stores the HTML templates for the website)*
            - __init__.py  *(Initialization script for the Flask application)*
            - auth.py  *(Manages user authentication routes)*
            - challenges.py  *(Manages the challenges of the game)*
            - manage_db.py  *(Manages the database)*
            - models.py  *(Defines the table models for the database)*
            - definition_score.py  *(Manages the definition score and stability system)*
            - views.py  *(Manages the routes and views of the game)*
            - database.db  *(SQLite database file to store the table and database of the game)*
        - main.py  *(Executable script to run the game)*




# Usage

## Prerequisites

The following libraries and packages are required for the project: 
- [nltk](https://pypi.org/project/nltk/) 
- [gensim](https://pypi.org/project/gensim/) 
- [flask](https://pypi.org/project/Flask/) 
- [owlready2](https://pypi.org/project/Owlready2/) 
- [numpy](https://pypi.org/project/numpy/) 
- [scikit-learn](https://pypi.org/project/scikit-learn/) 
- [networkx](https://pypi.org/project/networkx/) 
- [sqlalchemy](https://pypi.org/project/SQLAlchemy/) 

To install and set up the project, ensure that the mentioned libraries and packages are installed. You can easily install them using pip, for example:
```
pip install nltk gensim flask owlready2 numpy scikit-learn networkx sqlalchemy
```

## Installation

To run the game, follow these steps: 
1.  **Clone the Repository**: 
	- Clone the OntoQuest repository to your local machine using Git or download it: 
```
git clone https://github.com/NilsBarInf/OntoQuest.git 
```
2. **Navigate to the Flask Folder**: 
	- Navigate to the 'FLASK' directory in the cloned repository: 
```
cd VOCAB GAME/FLASK
``` 
3.  **Start the Game**: 
	- Open the `main.py` file and execute it to start the game: ``` python main.py ``` 
4.  **Access the Game**: 
	- Once the game is running, click on the HTTP address that appears in the terminal to open the game in a web browser. By following these steps, you can easily set up and start playing the OntoQuest game.
	
## Configuration

The project is currently in debug mode, but this can be deactivated by replacing the configuration with `debug=False` in the `main.py` file.

## Database Setup

All the **table models** are created in the `models.py` file and stored in the `database.db` file. To **add a new table** to the database, create one in the `models.py` file, and it will be automatically created and added to the database when launching the game. To **add a new row**, delete the entire table from the database, add the row to the table in the `models.py` file, and launch the game to recreate the table with the added row. To **access the database**, use DB Browser for SQLite.


# Additional Information

## Next Steps or Things Not Currently Implemented

-   Incentives such as challenges and badges
-   Improve the visualization of the ontology
