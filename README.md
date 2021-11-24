# inauthentic_twitter_nov2021
A scrape of high-volume inauthentic Twitter accounts from Nov. 2021

# Introduction
Follow-back behaviour on Twitter is not a new phenomenon, nor is it always used for malicious purposes. The follow-back Friday tradition has been running for over a decade, and has provided a mechanism for Twitter users to connect with other users sharing similar interests. However, follow-back mechanisms, when applied en-masse, via thousands of high-volume accounts is an indicator of inauthentic behaviour, and potentially automation. Although the existance of such high-volume follow-back mechanisms is well-known on Twitter, it is rarely the subject of investigation. The is because (i) Twitter's free API rate limits prohibit the sort of scraping required to properly capture all accounts involved in this activity, and (ii) the sheer size of these networks mean that crawling this space can take a very long time.

# Motivation
This particular attempt at defining the scope of an inauthentic follow-back group was prompted by an account I discovered while looking into COVID-related disinformation. The account, duncanclements6, is pictured below.

![](images/gooner2.jpeg)

An analysis of this account was conducted by botvolution and can be found here: https://twitter.com/botvolution/status/1463108224920571908

This fake account, disguised as a football fan from London, was heavily participating in the promotion of follow-back spam at the time of initial inspection. The account posted many tweets containing long lists of usernames, followed by a meme image, or short piece of text. This mechanism, in addition to being used to propagate large follow-back networks, was designed to fish for likes, retweets, and replies. And it worked all too well. In addition to posting its own follow-back-style tweets, it retweeted similar content, and often replied to follow-back-styled tweets, in order to promote them, or ask for follows. Scrolling through the account's timeline, it was observed that the duncanclements6 account repeatedly retweeted the same accounts that were also participating in similar username spam activities. A few of these were noted: Star7lt, USARGB, jAlmz5, duckusa, 8_27J, KeysLiisa, VuDeja4, emma6USA. The account had just been suspended at the time of writing, but it is unknown whether it was a temporary or permanent suspension.

At this juncture, it was hypothesised that there must be other accounts participating in this high-volume follow-back behaviour, and that manual analysis would be too cumbersome to identify them all. As such, some automation was created to explore this phenomenon, which is detailed in the next section.

# Methodology
A rudimentary script was created to search for additional accounts participating in this inauthentic activity. The script was designed to perform the following actions:
- obtain a Twitter screen_name from a list of unqueried accounts
- using the Twitter API, obtain that account's most recent 500 tweets
- iterate through captured tweets in order to identify tweets containing 7 or more account mentions
- if the criterion was met, check whether the tweet was original or a retweet
- record the url of the follow-back-style tweet, the screen_name of the account that published the original tweet, and a list of accounts mentioned in the tweet
- if the screen_name of the account that published the tweet wasn't on the list of unqueried accounts, append it
- repeat

Here is an example of a tweet matching the criterion:

![](images/example_followback_tweet.png)

The script was allowed to run for XXX hours between 11:00 November 24th 2021 and .

# Results
XXX Statistics gathered XXX
- number of accounts engaged in high-volume follow-back tweet behaviour
- number of tweets matching criteria
- number of unique accounts mentioned on user account lists in those tweets

The accounts involved in this network were observed to share COVID-related disinformation, anti-vax conspiracy theories, racist content, QAnon-related content, and extremist material. By-and-large the accounts are high-volume (publish hundreds of tweets per day) and have follower/following counts in the tens of thousands. Creation dates vary.

Some of the identified accounts have been actively participating in this behaviour for several years. For instance, the script discovered the PaulMer53 account, almost identical to a PaulMer52 account observed participating in pro-Brexit content amplification during the 2019 UK General election.

![](images/PaulMer53.png)
![](images/PaulMer52.png)

Also observed were accounts that auto-delete tweets at a rapid rate. For instance, according to Twitter's UI, this account has published 47.6k tweets. The script was ony able to obtain 175 tweets from the account, meaning that the rest were deleted, likely by automation.

![](images/LindaNTx.png)
