# Registering by Auto-Detection #
The file [open-search-generic.xml](http://gsa-open-search-via-opensearch.googlecode.com/files/open-search-generic.xml) gives you an idea of what an OpenSearch description file looks like in the Google Search Appliance. This file is the description for a so called OpenSearch provider. In order to allow a user to register this OpenSearch provider as a search plugin to the user's browser, you can adjust all the variables as described in the file [open-search-generic.xml](http://gsa-open-search-via-opensearch.googlecode.com/files/open-search-generic.xml) and upload it to a web server. If you then add this line
```
<link rel="search" type="application/opensearchdescription+xml" title="Google Search Appliance" href="URL_of_your_OpenSearch_description_file">
```
to any HTML page, most browsers will then auto detect the search provider that is described in the OpenSearch description file and provide the the user with the option to add it to the browser's search box.

![http://gsa-open-search-via-opensearch.googlecode.com/files/add-search-plugin-2.png](http://gsa-open-search-via-opensearch.googlecode.com/files/add-search-plugin-2.png)


But it would not be very GSA-like to make a separate web server a requirement. So we found a way to automatically generate the OpenSearch description file using the GSA's XSLT engine.

# Registering by Mouse Click #
This alternative makes it unnecessary to use a web server to host the OpenSearch description file, and moreover,  configuration of this file is no longer necessary. The GSA will generate the OpenSearch description file automatically using all the current parameters (front end, collection, filters, etc.).

Besides Auto Detection there is another way to register an OpenSearch provider using JavaScript. The code looks like this:
```
window.external.AddSearchProvider(url);
```

The following solution will add a button in the upper right corner of your search front end that will allow the user to add the search front with all its settings as a search provider to the user's browser.

![http://gsa-open-search-via-opensearch.googlecode.com/files/browser-integration-2.gif](http://gsa-open-search-via-opensearch.googlecode.com/files/browser-integration-2.gif)

If you use Google Chrome a dialog will be displayed as confirmation. You can enter a convenient keyword that will trigger the search to the GSA in the Omnibox (the combined URL and search box in Google Chrome).

![http://gsa-open-search-via-opensearch.googlecode.com/files/chrome-integration-1.png](http://gsa-open-search-via-opensearch.googlecode.com/files/chrome-integration-1.png)

After you have choosen a keyword (e.g. "gsa") you can choose the search provider by entering that keyword into the Omnibox and pressing the tab key. Google Chrome will then allow you to enter your query to the GSA into the Omnibox (query suggestions will be displayed).

![http://gsa-open-search-via-opensearch.googlecode.com/files/chrome-integration-2.png](http://gsa-open-search-via-opensearch.googlecode.com/files/chrome-integration-2.png)

# Installation #
## Step 1 ##
Create a new front end in your search appliance called "OpenSearchDescription" (using this exact spelling). Edit the front end setting and in the tab "Output Format" click on "Edit underlying XSLT code". Paste all the XSLT code from the file [OpenSearchDescription.xslt](http://gsa-open-search-via-opensearch.googlecode.com/files/OpenSearchDescription.xslt) into the text field. Save your changes.
## Step 2 ##
Edit the XSLT code of the front end where you want the "Add as Search Plugin" to appear. Find the code line
```
<xsl:template name="personalization">
```
Insert these three lines of code right beneath:
```
<div class="personalization" width="100%" align="right" style="font-size:84%;padding: 0 0 4px;">
	<xsl:text disable-output-escaping='yes'>&lt;a href='javascript:window.external.AddSearchProvider(document.location.href.replace(/proxystylesheet=([^&amp;]*)/g, "proxystylesheet=OpenSearchDescription&amp;originalproxystylesheet=$1") + "&amp;gsahost=" + document.location.protocol + "//" + document.location.hostname + "/");'&gt;Add as Search Plugin&lt;/a&gt;</xsl:text>
</div>
```
Click on the button "Save XSLT code".
# How it works #
When the user clicks on "Add as Search Plugin", the GSA will automatically create an OpenSearch description file by calling up the proxystylesheet "OpenSearchDescription". The JavaScript code will call up this proxystylesheet with all the parmeters of the current front end plus the two additional parameters "gsahost" and "originalproxystylesheet". These parameters are needed in order to create the OpenSearch description file dynamically.