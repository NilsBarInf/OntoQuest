# Introduction

## Description

**OntoQuest** is a *vocabulary management game* tailored to address the nuanced terminologies and vocabulary within **Infineon Technologies**. With diverse coverage across *Automotive*, *Green Industrial Power*, *Power & Sensor Systems*, and *Connected Secure Systems*, understanding the comprehensive vocabulary becomes a challenge. The game ensures domain-specific vocabulary definitions and terminology standardization, mitigating misunderstandings stemming from multiple meanings of the same words and discrepancies in cross-departmental communication.

## Process
The game's process begins with **domain or department selection**, followed by **ontology selection** and **question quantity**. Users engage in validating vocabulary *definitions*, presenting terms and their definitions, with options to **agree**, **disagree**, or express uncertainty. The completed definitions and *contribution scores* are summarized. The scoring system weighs agreement based on **previous agreements** and **community consensus**, while **disagreement** scoring accounts for *semantic differences*. The stability system utilizes *semantic similarity calculations*, dynamic stability thresholds based on **total reviews**, and **clustering** to consolidate definitions, ensuring coherence and consistency.

## Files Structure

- VOCAB GAME
    - .idea  *(IDE-specific directory for project settings and configurations)*
    - __pycache__
    - FLASK
        - instance  *(Flask instance folder for configuration files)*
        - website
            - static  *(Contains static assets such as CSS, JSON, images, and ontologies)*
                - css
                - json
                - ontologies  *(File to store the ontologies of the game as rdf file)*
                - picture *(File to store particularly the ontologies pciture)*
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
- [flask login](https://pypi.org/project/Flask-Login/)
- [owlready2](https://pypi.org/project/Owlready2/) 
- [numpy](https://pypi.org/project/numpy/) 
- [scikit-learn](https://pypi.org/project/scikit-learn/) 
- [networkx](https://pypi.org/project/networkx/) 
- [flask sqlalchemy](https://pypi.org/project/Flask-SQLAlchemy/)
- [rdflib](https://pypi.org/project/rdflib/4.0/)
- [SQL Alchemy](https://pypi.org/project/SQLAlchemy/)
- [Werkzeug](https://pypi.org/project/Werkzeug/)

To install and set up the project, ensure that the mentioned libraries and packages are installed. You can easily install them using pip and the provided requirements.txt file:
```
pip install -r requirements.txt
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

All the **table models** are created in the `models.py` file and stored in the `database.db` file. To **add a new table** to the database, create one in the `models.py` file, and it will be automatically created and added to the database when launching the game. To **add a new row**, delete the entire table from the database, add the row to the table in the `models.py` file, and launch the game to recreate the table with the added row. To **access the database**, use [DB Browser for SQLite](https://sqlitebrowser.org/).

# Introduction to Flask
[Flask](https://pymbook.readthedocs.io/en/latest/flask.html) is a web framework for Python, known for its simplicity and flexibility. It facilitates the creation of web applications and RESTful APIs. In OntoQuest, Flask is used to handle web requests, render HTML templates, and serve static assets such as CSS and JavaScript.

## Route/Page
To add a new route/page in Flask, you can define a new function with the `@views.route` decorator in the `views.py` file. This function will handle HTTP requests for a specific URL path and return the corresponding response.

*Example: Adding a New Page and Linking it to HTML*
```
@views.route('/new-page', methods=['GET'])
def new_page():
    return render_template('new_page.html')
```

## HTML 
In Flask, you can use the `render_template` (see previous example) function to render HTML templates. This function takes the name of the HTML template as an argument and renders the template with any necessary context data. In a Flask application, an HTML template is a file that contains the structure and content of a web page. It allows you to dynamically generate HTML by inserting data from your Python code into the template.

*Example: HTML Template*
```
{% extends "base.html" %}
<!-- This template extends a base template, allowing you to reuse common HTML structure and styling
	across multiple pages.  -->

{% block title %}New Page{% endblock %} <!-- Your Page Title Here -->

{% block styles %}
    <!-- Link to your custom CSS file or any other code for the style of your HTML page -->
    <link rel="stylesheet" type="text/css" href="{{ url_for('static', filename='css/your-styles.css') }}">
{% endblock %}

{% block content %}
    <!-- Content specific to your page -->
                <!-- Example of Python loop to generate range of values -->
                {% for i in range(0, 11) %}
                    <span>{{ i*5 }}</span>
                {% endfor %}
{% endblock %}
```

## Creation Guidelines
When creating a new route/page, you need to create the corresponding HTML and CSS files. The HTML file should be placed in the `templates` directory, and the CSS file should be placed in the `static/css` directory. This ensures that Flask can locate and serve these files correctly.

# Ontologies Management

## Ontologies File Structure
When adding an ontology to the game, store the RDF file in the ontologies directory, which is a subdirectory of the static file. Currently, only RDF file types are supported.

## Ontology Format Guidelines
To ensure compatibility, follow these guidelines when creating or editing ontologies:

- Each term should be represented as a class.
- Define each term's definition as an annotation, specifically a comment, associated with the corresponding class.
- The additional information provided by the users are stored with data properties that are the following one:
	- hasAbbreviation
	- hasAlternativeName
	- hasExample
	- hasGermanName
## Database Configuration
In addition to adding the ontology file, you need to register the ontology in the database. You can do this using a database browser or by running the necessary SQL commands.

### Ontology Table
Add a new row to the `ontology` table with the following information:
- name: The name of the ontology
- description: A brief description of the ontology
- image_url: The URL to the corresponding image of the ontology, in the format `picture/name_of_image.jpg`
- ontology_url: The name of your ontology file, in the format `name_of_ontology.rdf`

### Department-Ontology Association
To associate the ontology with the relevant departments, add the necessary rows to the `department_ontology_association` table with the following information:
- department: The name of the department
- ontology_id: The ID of the ontology you previously added to the ontology table

## Updating Departments

When adding or modifying an existing department, you need to update the `department_ontology_association` table accordingly. Additionally, you need to update the `department.html` file by adding or modifying the following code with the department's name that you entered in the DB as value:

```
<option value="name_of_department">Name of Department</option>
```

By following these steps, you can successfully add an ontology to the game and make it playable for the associated departments.

# Additional Information

## Next Steps or Things Not Currently Implemented

-   Incentives such as challenges and badges

