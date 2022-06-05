# RSSCacheDetectionChallenge

Background:

The primary source of recently published articles for Company X are typically RSS and/or Atom feeds, which are polled by Company X approx. every 60 seconds. Refreshing a feed with new content is typically a slow process given the number of articles some brands create so it is very common for customers to cache their feeds. The consequence of caching is that new articles will generally appear at fixed intervals, instead of the moment at which they are each published. This leads to Company X receiving content too late and therefore offering a less real-time user experience. It is important that Company X can automatically detect when the caching is greater than 10 minutes so that Company X can ask customers to reduce the caching interval.

This problem is complicated by the fact that some feeds have invalid ‘publish times’. We have the following two type of feed:

Normal - All publish times can be considered valid. The publish time reflects that provided by the RSS/Atom feed (i.e. the time at which the article was first accessible online). This will typically be shortly before Company X first sees the article (time created).
Bad Publish Time - Publish times are considered invalid. The publish time of articles parsed from this type of feed are assumed to be random (or equal to the time created). The only reliable piece of information associated with articles from these feeds is the time created field (i.e. when Company X first saw the article).

We have provided sample data sets of many different feeds (each of which represents 30 days worth of articles in CSV format), including a skeleton java project framework (if you choose to develop a solution using Java), which can be downloaded here. Each entry (an account article source) in these data represents a new article being published in a feed with a corresponding time published and time created. This download bundle also includes a CSV parser that you may use to quickly import the data. The execution entry point into this sample project is Application.main(String[]).

Note: The data files within the download bundle are located at RSSCacheDetection/ACCOUNT_ARTICLE_SOURCES

Note2: The provided data contain two trivial examples of feeds WITH and WITHOUT caching, to further clarify what ‘caching is’. The example files are located at RSSCacheDetection/ACCOUNT_ARTICLE_SOURCES/EXAMPLES

The challenge:

Develop a solution, using the tools of your choice, that given a list of account article sources, and the type of feed, attempts to estimate whether there is a caching interval, and if yes, what it is. If you wish you may use different solutions for the two different types of feed explained above.

Note: All times in the sample data are unix times (https://en.wikipedia.org/wiki/Unix_time)

Note2: If the caching interval is less than 10 minutes (600 seconds) you can consider this to be equivalent to NO CACHING.

Caching interval is defined as:
Time period between changes made to the website appearing in the RSS feed. i.e. changes are made to the website all of the time at random periods, but the RSS feed may only update (refresh) every 15 minutes.

Another way of thinking about it is that the RSS feed shows a point in time snapshot of the latest changes to a website, this snapshot will only be refreshed every x minutes if there was a change. That x is the cache interval.


The outcome of this challenge should be a table of feeds, preferably as a standalone CSV file, (the feed identifier is the numerical postfix on all of the sample data) where you state if the feed is considered cached (> 600 secs) and what the caching interval is (in seconds), e.g:

FeedIdentifier
Caching?
CachingInterval
101
False
0
102
False
60
103
True
600


Please use this format as it makes it quicker for us to evaluate your submission, here’s a sample CSV file - link.

Additional notes:
If you have time make sure you consider handling outliers from real data robustly.
Visualisations can be helpful to explain some of your choices so feel free to include them.
The CSV file should only contain numerical or boolean (True/False) values. If there is not enough data to determine whether the feed is cached or not, you can consider that the feed is not cached and the caching interval is 0.
Libraries:

You are free to use whatever libraries you wish.
