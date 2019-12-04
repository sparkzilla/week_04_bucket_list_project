# Mark's Bucket List App #

**User Input**

The app allows a user to add, edit sights, and update the status of sights.

The user inputs a sight, city and country all at one time, they cannot enter cities or countries independently.

If an existing city or country exists, the system will assign the existing city_id or country_id to the record. However, as the fields are free input, there is no validation to stop a user adding variations ("UK", "United Kingdom" will generate separate results).

The user can update the status. I used the *redirect back* Sinatra command to redirect back to the page the update happened on.

**Map Display**

Sights are displayed on an image generated from [MapQuest Static Maps API](https://developer.mapquest.com/documentation/static-map-api/v5/getting-started/). This allows maps to be generated with no Javascript.

Visited sights are displayed as green dots, Bucket List sights are displayed in red.

The image is generated by constructing a url, comprising a *map_url*, which comprises the API url, the API access key, and a list of locations, which are generated by looping through the sight objects and appending them to the url.

Basic url encoding (changing commas and spaces) is required to create a valid url. the url is then simply added as the *src* for an *img* tag.

The Map API is not that accurate, so sometimes in detail views the location is incorrect. This is probably because the system is skewed towards US addresses.

**CSS**

Select boxes for status(visited/bucket) are styled to change colour based on the selection.

I don't understand flex, so I did not use it. I will learn it before the next project.

**Issues**

The long *map_url* in the controllers should be put in a class. I tried this, but it did not work.

Validation for the input form (in the /sights/ POST controller) should be moved into a separate function.

Should probably do the URL encoding as a separate function

**Potentials**

I wanted to add images for each of the site, city and country detail pages, using Google Places API, but it required the http-get gem. I may give it a go outside the project.

Update to Google Maps API, to create interactive maps, would require javascript.
