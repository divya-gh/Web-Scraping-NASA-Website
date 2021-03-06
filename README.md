# web-scraping with beautifulSoup
Scrapping NASA website with BeautifulSoup , Data wrangling with pandas , Data storage and App creation with MongoDB and Flask API


## Table of contents
* [Project Title ](#project-title)
* [Description](#description)
* [Objective](#objective)
* [Screen Shots](#screen-shots)
* [Technologies](#technologies)
* [Code](#code)
* [Status](#status)
* [Acknowledgement ](#acknowledgement )
* [Contact](#contact)



## Project Title : Mission to Mars 

### Description : This project aims at building a web application that scrapes various websites for data related to __The Mission to Mars__ and displays the information in a single HTML page.

## Data Sources
	
- [NASA Mars News](https://redplanetscience.com/)
- [JPL Mars Space Images - Featured Image](https://spaceimages-mars.com/)
- [Mars Facts](https://galaxyfacts-mars.com/)
- [Mars Hemispheres](https://marshemispheres.com/)

## Objective

### Step 1 - Scraping:

- Scrape the [Mars News Site](https://redplanetscience.com/)
 and collect the latest News Title and Paragraph Text. Assign the text to variables that you can reference later.
- Using splinter navigate through [JPL Mars Space Images - Featured Image](https://spaceimages-mars.com/) and find the image url for the current Featured Mars Image.
- Visit the [Mars Facts](https://galaxyfacts-mars.com/) webpage and use Pandas to scrape the table containing facts about the planet including Diameter, Mass, etc. and use Pandas to convert the data to a HTML table string.
- Visit the [astrology](https://marshemispheres.com/) site to obtain high resolution images for each of Mar's hemispheres and create a dictionary.

### Step 2 - MongoDB and Flask Application:
- Use MongoDB with Flask templating to create a new HTML page that displays all of the information that was scraped from the URLs above.
	- convert your Jupyter notebook into a Python script with a function called scrape that returns one Python dictionary containing all of the scraped data.
	- create a route called /scrape that will import your scrape_mars.py script and call your scrape function.
	- Store the return value in Mongo as a Python dictionary.
	- Create a root route / that will query your Mongo database and pass the mars data into an HTML template to display the data.
	- Create a template HTML file called index.html that will take the mars data dictionary and display all of the data in the appropriate HTML elements.

## Screen Shots
![Final App](./Missions_to_Mars/Images/final_app.png)


 
## Technologies and Tools
* Jupyter Notebook
* Visual Studio code editor
#### Python Libraries
* pandas
* flask/jinja
* Web Scraping libraries
	* Splinter
	* Requests
	* BeautifulSoup4
	* webdriver_manager
	
	

## Code 
- [mission_to_mars.ipynb](/Missions_to_Mars/mission_to_mars.ipynb)
- [scrape_mars.py](/Missions_to_Mars/scrape_mars.py)
- [Flask app.py](/Missions_to_Mars/app.py)


## Setup
1. Git clone this repository
2. Open [Flask app.py](/Missions_to_Mars/app.py) in Visual code editor
4. Execute the code to launch chrome browser containing scraped data from NASA's Mars sites.

## Status
Project Complete

## Acknowledgement 
- UTSA BootCamp


## Contact
 [Divya Shetty](https://github.com/divya-gh)
 
