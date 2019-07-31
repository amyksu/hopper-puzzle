# hopper-puzzle

## Challenge Accepted

While browsing jobs yesterday, I came across a Data Scientist opening at Hopper. Being an active user of the app, I got excited and was even more excited when I saw a puzzle link in the job description. 

For those of you who don’t know, Hopper is a flight-booking app that predicts flight prices with 95% accuracy up to 1 year in advance telling users when they should buy or wait for a better price. To get this kind of accuracy, Hopper not only gathers historical data for their predictions, but also aggregates the results of current fares across multiple search engines and uses this information to determine the best deals being booked at any given moment. 


## Results

In the job description, the line goes, “At Hopper, every dataset tells a story. Do you have what it takes to decipher the clues?” When you click on the link, a google document loads and you just see two columns on numbers. My first thought was, “These are for sure longitude and latitude pairs”. The thing was that the numbers seemed a little low. Not to be deterred, I continued on and started my analysis. For all of my code, please check out my [jupyter notebook](https://github.com/amyksu/hopper-puzzle/blob/master/code/Hopper%20Puzzle.ipynb). 

To confirm or deny my hypothesis, I decided to do some exploratory data analysis (EDA) and plotted the data in a scatterplot using Seaborn (shown below): 


![](https://paper-attachments.dropbox.com/s_7703D9EE56AB2E38D4B7340FB7A67D8094BF790511E8E93F9B55CE9D70624D91_1564611732548_image.png)


Looking at the right side of the plot, it was pretty clear to me that we were looking at the United States. Now that I knew that the data was latitude and longitude values in radians, I decided to plot the data using Basemap and Tableau (see below):


![](https://paper-attachments.dropbox.com/s_7703D9EE56AB2E38D4B7340FB7A67D8094BF790511E8E93F9B55CE9D70624D91_1564612752844_image.png)

<sup> For interactive Tableau Map, [click here](https://10ay.online.tableau.com/t/amyksu/views/HopperPuzzle/InitialDataPlot?iframeSizedToWindow=true&:embed=y&:showAppBanner=false&:display_count=no&:showVizHome=no&:origin=viz_share_link).</sup>

Looking at the map and having previously worked with the Bureau of Transportation Statistics flight delays dataset, it appears to me that based on the United States portion, this dataset lists the latitude and longitude pairs of airports. 

With this hypothesis in mind, I found a dataset (from openflights.org) of all of the latitude and longitude pairs of airports globally. Using this, I matched the dataset found on the Hopper job description to the airport dataset to see if the pairs match, and they did! Now that I knew that they were airports, I did some more EDA and found that there was over 100 flights from Taitung Airport in Taiwan while everywhere else had one or two flights. I guessed that this meant that the data was probably listing out flight paths, and here’s what I ended up with: 


![](https://paper-attachments.dropbox.com/s_7703D9EE56AB2E38D4B7340FB7A67D8094BF790511E8E93F9B55CE9D70624D91_1564613274150_image.png)

<sup> For interactive Tableau Map, [click here](https://10ay.online.tableau.com/t/amyksu/views/HopperPuzzle/FlightRoutes?iframeSizedToWindow=true&:embed=y&:showAppBanner=false&:display_count=no&:showVizHome=no&:origin=viz_share_link).</sup>

In my plot above, the larger blue bubbles and lines indicates more flights going in and, or out of that airport. The smaller coral bubbles and lines indicates less flights.

Following the clues, I believe I landed upon a dataset that shows flight paths. However, contrary to my last hypothesis, I believe this dataset include multiple outgoing airports not just Taitung. With more information, I'd love to see if I could find more trends and information out of these flight patterns. 
