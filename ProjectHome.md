# GSA open search via OpenSearch #
OpenSearch is a collection of simple formats for the sharing of search results. The OpenSearch description document format can be used to describe a search engine so that it can be used by search client applications. Such search client applications include all major browsers and the Explorer Window in Win 7.
Among such search client applications are all major browsers, the Explorer window in Windows 7 being the most prominent. See http://www.opensearch.org/ for more information about OpenSearch.

This project provides you with all resources you need to connect your **Google Search Appliance** (GSA) with an OpenSearch client such as Windows 7 federated search or any of the major browsers. What you get is:
  * a generic example of an OpenSearch description file ([open-search-generic.xml](http://gsa-open-search-via-opensearch.googlecode.com/files/open-search-generic.xml))
  * an OSDX file for Windows 7 ([open-search-win7.osdx](http://gsa-open-search-via-opensearch.googlecode.com/files/open-search-win7.osdx))
  * an XSLT file that converts the GSA's XML results to an RSS feed file that can be processed by your OpenSearch client ([rss.xslt](http://gsa-open-search-via-opensearch.googlecode.com/files/rss.xslt))
  * an XSLT file that will dynamically create an OpenSearch description file on the GSA. That way your users can register the GSA as search plugin. ([OpenSearchDescription.xslt](http://gsa-open-search-via-opensearch.googlecode.com/files/OpenSearchDescription.xslt))

### Windows 7 Integration ###
If your Intranet content (e.g. Windows file shares or SharePoint) have been indexed by a GSA, all Windows clients will be able to submit search queries from the Windows Explorer. Read more about this scenario [here](http://code.google.com/p/gsa-open-search-via-opensearch/wiki/Windows7Integration).

![http://gsa-open-search-via-opensearch.googlecode.com/files/win7-integration-3.gif](http://gsa-open-search-via-opensearch.googlecode.com/files/win7-integration-3.gif)

### Browser Integration ###
If you want to submit search queries right from your browser (**Firefox, Internet Explorer, Google Chrome**), you can register the GSA as a search provider. Read more about this scenario [here](http://code.google.com/p/gsa-open-search-via-opensearch/wiki/BrowserIntegration).

![http://gsa-open-search-via-opensearch.googlecode.com/files/add-search-plugin-2.png](http://gsa-open-search-via-opensearch.googlecode.com/files/add-search-plugin-2.png)
