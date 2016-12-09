# Power Plant Cooling Systems
*Written in Python v2.7.11. Please install [openpyxl](https://openpyxl.readthedocs.io/en/default/) library to read Excel. Please install [SQLite Browser](http://sqlitebrowser.org/) if you wish to view and modify the databases (optional).*

The scrip `solution.py` does the following:

1. Reads Excel files and create databases of cooling types and geographic coordinates information of power plants.
2. Create a folder for each cooling type.
3. Uses [Google Static Maps API](https://developers.google.com/maps/documentation/static-maps/intro) to find satellite images of the plants.
4. Save images in the folder of the corresponding cooling type.

To avoid wasting rate limit, the program fires a new query through API only when the image has never been downloaded before, i.e., does not exist in any folder.

For each run, the program will check if the image already exists in folder or not. If yes, then the program will not consume the Google API. In the case where a power plant has multiple cooling types, the program will download image for one cooling folder, and copy the image to the other cooling folders. For example, plant Barry has two types of cooling systems: Once through cooling and Recirculating. The program will retrieve the plant satellite image to the Once through cooling folder, and copy the image file to the Recirculating folder instead of downloading a new one.

Run `solution.py` to start downloading images. All the images will be saved in the folder `images`. You can change 'countLimit' to limit the number of queries per run. Please note that the with current API key, the number of free queries is rate limited 2500 per day.
