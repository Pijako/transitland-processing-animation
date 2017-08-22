# Transitland Processing Animation (work in progress)
Animating scheduled transit trips using the [Transitland API](https://transit.land/) from Mapzen and the [Processing](https://processing.org/) language with the [Unfolding Maps](http://unfoldingmaps.org/) library.

Here is an example animation generated for the Bay Area:

[![IMAGE ALT TEXT](http://i.imgur.com/kkOxCil.png)](https://vimeo.com/226987064 "Transit Flow Map of San Francisco Bay Area")

### Set up Processing:
1. Download [Processing 3](https://processing.org/).
2. Download [Unfolding Maps version 0.9.9 for Processing 3](http://services.informatik.hs-mannheim.de/~nagel/GDV/Unfolding_for_processing_0.9.9beta.zip).
3. Navigate to `~/Documents/Processing/libraries` on your machine.
4. Drag and drop the unzipped Unfolding Maps folder into `~/Documents/Processing/libraries`.
5. Open Processing, navigate to Sketch > Import Library > Add Libary. Search for "Video Export" and click Install.
6. Quit and re-open Processing.

### Instructions:
- `git clone https://github.com/transitland/transitland-processing-animation.git`

To run with virtualenv (optional, recommended):
- `virtualenv virtualenv`
- `source virtualenv/bin/activate`

Install python requirements:
- `python virtualenv/bin/pip install -r requirements.txt`

Navigate to folder:
- `cd transitflow`

Visualize transit flows by operator onestop_id:
- `python transitflow.py --date=2017-08-15 --name=bart --operator=o-9q9-bart`

Visualize transit flows by bounding box:
- `python transitflow.py --date=2017-08-15 --name=sacramento --bbox=-121.640625,38.466493,-121.297302,38.683366`

Bay area:
- `python transitflow.py --date=2017-08-15 --name=bay_area --bbox=-123.280334,37.011326,-120.607910,38.955137 --clip_to_bbox --exclude=o-9-amtrak,o-9-amtrakcharteredvehicle`

Vancouver:
- `python transitflow.py --date=2017-08-15 --name=vancouver --bbox=-123.441010,49.007249,-122.632141,49.426160 --clip_to_bbox`

Atlanta:
- `python transitflow.py --date=2017-08-15 --name=atlanta --bbox=-84.880371,33.321349,-83.908081,34.198173 --clip_to_bbox`

Los Angeles:
- `python transitflow.py --date=2017-08-15 --apikey=mapzen-ai1duha --name=los_angeles --bbox=-119.448853,32.925707,-116.768188,34.664841 --clip_to_bbox`

### Room for future improvements...
- The Processing sketch currently uses simple linear interpolation to animate a point from stop A to stop B given the departure and arrival times. It does not show vehicles following their actual, real-life routes. The sketch would be more meaningful if vehicles actually followed their routes. This seems entirely possible to do for operators that provide route shapes... just haven't gotten there yet!

### Known issues:
- Python script is running into API timeouts and failing to process some of the biggest transit operators, including NYC MTA and Chicago Transit Authority.
- Bay Area script is failing to download the Santa Cruz Metro due to an API issue (work in progress)

### Credits:
- Data: [Mapzen](https://mapzen.com/), [Transitland](https://transit.land/)
- Basemap: Carto, OpenStreetMap
- Processing Code: The Processing code builds off [this workshop](https://github.com/juanfrans-courses/DataScienceSocietyWorkshop) by [Juan Francisco Saldarriaga](http://juanfrans.com/), a researcher at the Center for Spatial Research at Columbia University and an adjunct assistant professor of urban planning and architecture. It also relies on the [Unfolding Maps](http://unfoldingmaps.org/) library for converting geolocations to screen positions. Unfolding Maps was created and is primarily maintained by [Till Nagel](http://tillnagel.com/), a professor of visual analytics at University of Applied Sciences Mannheim.

### Sources of inspiration:
- *[Shanghai Metro Flow](http://tillnagel.com/2013/12/shanghai-metro-flow/)*, Till Nagel
- *[Barcelona Cycle Challenge](http://juanfrans.com/projects/barcelonaCycleChallenge.html)*, Juan Francisco Saldarriaga
- *[Seven Days of Carsharing in Milan](http://labs.densitydesign.org/carsharing/))*, Matteo Azzi, Daniele Ciminieri, others
- *[NYC Taxis: A Day in the Life](http://chriswhong.github.io/nyctaxi/)*, Chris Whong

And here are a few that I've made in the past using similar methods:
- *[Multimodal Symphony: 24 Hours of Transit in New York City](https://vimeo.com/212484620)*, Will Geary
- *[Los Angeles Transit Flows](https://vimeo.com/227178693)*, Will Geary
- *[California Transit Flows](https://vimeo.com/227178693)*, Will Geary
- *[New York City Taxi Flows](https://vimeo.com/210264431)*, Will Geary
- *[New York City Subway Flows](https://vimeo.com/194378581)*, Will Geary
