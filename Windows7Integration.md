## Instructions ##

### ...to OpenSearch-enable your GSA ###
  1. Download the file [rss.xslt](http://gsa-open-search-via-opensearch.googlecode.com/files/rss.xslt).
  1. Adjust the XSLT variables _gsa\_base\_url_ and _html\_hit\_highlighting_ as described in the comments.
  1. Create a new front end in your GSA and name it "rss". Edit the front end and in the tab "Output Format" click on "Edit underlying XSLT code". Completely replace the existing XSLT code with the content of the modified file [rss.xslt](http://gsa-open-search-via-opensearch.googlecode.com/files/rss.xslt). Then click on the button "Save XSLT Code"

Your GSA is now ready to serve search results in the rss format via this front end as required by Windows 7.

### ...to register the GSA in Windows 7 client ###
  1. Download the file [open-search-win7.osdx](http://gsa-open-search-via-opensearch.googlecode.com/files/open-search-win7.osdx) and modify it as described in the XML comments. Make sure that you replace the value of the parameter "proxystylesheet=..." with the name of the front end you have created as described before - we assume that you called the front end "rss".
  1. In Windows 7 just double click on the OSDX file and Windows 7 will register the GSA as additional federated search provider.

![http://gsa-open-search-via-opensearch.googlecode.com/files/win7-integration-1.gif](http://gsa-open-search-via-opensearch.googlecode.com/files/win7-integration-1.gif)

### About Secured Search ###
Due to the non-standard behavior of Windows 7, it is not possible to display secured results within an explorer window. This is why you should not add a URL parameter &access=a or &access=s to the search query URL. However the OSDX file also contains a definition for a HTML version of search results.
```
<Url type="text/html" ... template="http://....
```
This is why Windows 7 displays a button "Search on website" in the explorer window. Clicking that button will open the standard browser and display the search results in that browser. You can add the parameter &access=a to the URL in the template attribute since the browser will speak the required security protocols (HTTP Basic, NTLM, SAML, Kerberos, etc.) and then also display secured results.

![http://gsa-open-search-via-opensearch.googlecode.com/files/win7-integration-2.gif](http://gsa-open-search-via-opensearch.googlecode.com/files/win7-integration-2.gif)