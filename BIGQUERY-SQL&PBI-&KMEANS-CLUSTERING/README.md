**Project Name:** Search Trends Tool

**Description:** Dynamic tool with refreshable data. Leverages a blended data model of Power BI 'Google Big Query' data source connection and Python data source connection that layers a column for k-means cluster (MiniBatchMeans) into Big Query pull of Wikipedia page title and their respective view count for time-period in-scope. Leverage BigQuery public datasets and open source python packages.

**Installation Instructions:** Download pbix file. Adjust Python code to reference your own Google application credentials. Remove 'FilteredRows' steps in power query editor to unlock full scope of each dataset (limits were applied to make the file small enough to upload here)

**Usage:** This is a refreshable model that allow you to keep a finger on the pulse of rising search trends in both Google and Wikipedia. The Wikipedia K-means clusters utilize natural language processing and unsuporvised machine learning to categorize the titles (The dataset does not inherently come with a category dimension); which types of titles get the most views? (ex: entertainment vs education).

**Contact Information:** troy.schiebel@gmail.com
