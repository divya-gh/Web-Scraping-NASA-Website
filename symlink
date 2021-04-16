from flask import Flask, render_template, redirect
from flask_pymongo import PyMongo
import scrape_mars as ms

# create instance of Flask app
app = Flask(__name__)

# Use flask_pymongo to set up mongo connection
app.config["MONGO_URI"] = "mongodb://localhost:27017/mars_app"
mongo = PyMongo(app)

# create a main route that renders index.html template
@app.route("/")
def index():
    mars_news = mongo.db.news.find_one()
    return render_template("index.html", mars_news= mars_news)

# Call scrape function from scrape_mars.py file and load mongo DB
@app.route("/scrape")
def scraper():
    # create a collection
    news = mongo.db.news
    # get data from the scrape_mars.py file
    mars_data = ms.scrape()
    # Update Mongo collection with new data 
    # Note: {} - update all upsert- insert if not there or update entire collection if there
    news.update({}, mars_data, upsert=True)
    return redirect("/", code=302)


if __name__ == "__main__":
    app.run(debug=True)
