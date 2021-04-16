
from splinter import Browser
from bs4 import BeautifulSoup
from webdriver_manager.chrome import ChromeDriverManager
import requests
import pandas as pd


# define the function to return srapped values

def scrape():
    # Setup splinter
    executable_path = {'executable_path': ChromeDriverManager().install()}
    browser = Browser('chrome', **executable_path, headless=False)

    # Define url  and set up config splinter to the site 
    #Create a function that takes the url and return the soup 
    def create_soup(url):
        browser.visit(url)
        # Create BeautifulSoup object; parse with 'html.parser'
        html = browser.html
        soup = BeautifulSoup(html, 'html.parser')
        return soup



    # ### -------------------------------------------------------------------------------------------------------------------------------####
    # #### NASA Mars News
    #     - Scrape the Mars News Site and collect the latest News Title and Paragraph Text.
    # ### -------------------------------------------------------------------------------------------------------------------------------####


    #Define the url to visit and call the function create_soup
    url = 'https://redplanetscience.com/'
    soup = create_soup(url)


    # grab the title
    title = soup.find('div' , class_="content_title").text
    




    # Grab the paragraph
    news_p = soup.find('div', class_="article_teaser_body").text
    


    # ### -------------------------------------------------------------------------------------------------------------------------------#####
    # #### JPL Mars Space Images - Featured Image
    #     - Visit the url for the Featured Space Image site https://spaceimages-mars.com/
    #     - Find the image url to the full size .jpg image.
    # ### -------------------------------------------------------------------------------------------------------------------------------#####

   

    # Define url  and call create_soup function to return soup 
    featured_url = 'https://spaceimages-mars.com/'
    soup = create_soup(featured_url)



    # Create BeautifulSoup object; parse with 'html.parser' to the second site
    try:
        target = 'button[class="btn btn-outline-light"]'
        browser.find_by_tag(target).click()
        html = browser.html
        soup = BeautifulSoup(html, 'html.parser')
        image_src = soup.find('img', class_="fancybox-image")['src']
    except:
        print('can\'t find the image')
    featured_image_url = featured_url + image_src


    # ### -------------------------------------------------------------------------------------------------------------------------------###
    # #### Mars Facts
    #         - Visit the Mars Facts webpage https://galaxyfacts-mars.com/ and use Pandas to scrape the table 
    #           containing facts about the planet including Diameter, Mass, etc.
    #         - Use Pandas to convert the data to a HTML table string.
    # ### -------------------------------------------------------------------------------------------------------------------------------###



    # define url to visit
    mars_facts_url = 'https://galaxyfacts-mars.com/'
    # using pandas read html
    tables = pd.read_html(mars_facts_url)
    # find total no. of tables in the list
    len(tables)



    # check for the table in iterest and select that table
    mars_fact_df = tables[0]
    mars_fact_df


    # In[11]:


    # add column names ['Description' , 'Mars', 'Earth']
    mars_fact_df.columns = ['Description' , 'Mars', 'Earth']

    # set Description as a index
    mars_fact_df.set_index('Description' , drop=True , inplace= True)
    mars_fact_df


    # In[12]:


    # Save the table in HTML format
    mars_fact_df.to_html('table.html', classes="table table-bordered border-dark table-success table-striped align-left")
    table = mars_fact_df.to_html(classes="table table-bordered border-dark table-success table-striped vertical-align-left")
    table = table.replace('\n','')
    

    # ### -------------------------------------------------------------------------------------------------------------------------------####
    # #### Mars Hemispheres
    #           - Visit the astrogeology site here to obtain high resolution images for each of Mar's hemispheres.
    #           - get image url to the full resolution image.
    # ### -------------------------------------------------------------------------------------------------------------------------------####



    # Define the url and call create_soup function to return soup object
    mars_hem_url = 'https://marshemispheres.com/'
    soup = create_soup(mars_hem_url)

    # Find the container that holds all the images in the main page
    container = soup.find_all('div' , class_="item")

    # Initialize the list
    hemisphere_image_urls =[]

    for content in container:    
        # use splinter to navigate to the page to get the image file 
        # Note: splinter uses main browser not the cotainer so be specific
        h3 = content.find('h3').text
        
        browser.find_by_text(str(h3)).click()
        
        # get html of rendered page and create a soup
        html = browser.html
        soup = BeautifulSoup(html, 'html.parser')   
        
        # Get the title and the image link
        title_hem = soup.find('h2' , class_="title").text
        
        image = mars_hem_url + soup.find('img', class_="wide-image")['src']
        #print(image)
        
        #create a dictionary
        hemisphere_image_urls.append({
                                'title' :title_hem,
                                'img_url':image
                                })

        # go back to the original page to grab more data
        browser.back()        
      

    # Close the browser
    browser.quit()
    
    # create a dictionary of scrapped data
    mars_data = {
                'news_title' : title,
                'news_p':news_p,
                'featured_image':featured_image_url,
                'hemisphere_image_urls':hemisphere_image_urls,
                'table': table
                 }

    return mars_data
        

