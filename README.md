# inauthentic_twitter_nov2021
A scrape of high-volume inauthentic Twitter accounts from Nov. 2021

# Introduction
Follow-back behaviour on Twitter is not a new phenomenon, nor is it always used for malicious purposes. However, follow-back mechanisms, when applied en-masse, via thousands of high-volume accounts can be an indicator of inauthentic behaviour and potentially automation. Although the existance of such high-volume follow-back mechanisms is well-known on Twitter, it is rarely the subject of investigation. The is because (i) Twitter's free API rate limits prohibit the sort of scraping required to properly capture all accounts involved in this activity, and (ii) the sheer size of these networks mean that crawling this space can take a very long time.

This short report details the methodology used to capture members of a high-volume follow-back group, and includes data as a starting point that we hope Twitter's Safety team will act upon.

# Motivation
The motivation to define the scope of an inauthentic follow-back group was prompted by an account I discovered while looking into COVID-related disinformation. The account, duncanclements6, is pictured below.

![](images/gooner2.jpeg)

An analysis of this account was conducted by botvolution and can be found here: https://twitter.com/botvolution/status/1463108224920571908

This fake account, disguised as a football fan from London (but actually operated from the US), was responsible for the heavy promotion of follow-back spam at the time of initial inspection. The account posted many tweets containing long lists of usernames, followed by a meme image, or short piece of text. This mechanism, in addition to being used to propagate large follow-back networks, was designed to fish for likes, retweets, and replies. In addition to posting its own follow-back-style tweets, it retweeted similar content, and often replied to other follow-back-styled tweets asking for follows. Scrolling through the account's timeline, it was apparent that the duncanclements6 account repeatedly retweeted the same accounts that were also participating in similar username spam activities. A few of these were noted via manual inspection: Star7lt, USARGB, jAlmz5, duckusa, 8_27J, KeysLiisa, VuDeja4, and emma6USA. 

The account had just been suspended at the time of writing, but it is unknown whether it was a temporary or permanent suspension.

At this juncture, it was hypothesised that there must be other accounts participating in this high-volume follow-back behaviour, and that manual analysis would be too cumbersome to identify them all. As such, automation was created to explore this phenomenon.

# Methodology
A rudimentary script was created to search for additional accounts participating in this inauthentic activity. The script was designed to perform the following actions:
- obtain a Twitter screen_name from a list of unqueried accounts
- using the Twitter API, obtain that account's most recent 500 tweets
- iterate through captured tweets in order to identify tweets containing 7 or more account mentions
- if the criterion was met, check whether the tweet was original content or a retweet
- record the url of the follow-back-style tweet, the screen_name of the account that published the original tweet, and a list of accounts mentioned in the tweet
- if the screen_name of the account that published the tweet wasn't on the list of unqueried accounts, append it
- repeat

Here is an example of a tweet matching the criterion:

![](images/example_followback_tweet.png)

The script was allowed to run for XXX hours between 11:00 November 24th 2021 and . Note that the script was terminated before it had been able to query all accounts. As such, the data collected cannot be considered exaustive. Many more participants likely exist that were not discovered during this process.

# Results and discussion
The following statistics were gathered.
1. The number of accounts engaged in high-volume follow-back tweet behaviour identified during the script's run was XXX. A full list of Twitter user id_str values for these accounts can be found in this repository in a file named fbid.json. It is safe to assume that automatic suspension or deletion of accounts on this list can be performed by the Twitter Safety team.
2. The number of tweets matching the script's criteria was XXX remember to make it a set to remove duplicates, and re-save it XXX. The full list of tweet urls can be found in this repository in a file named urls.txt. This file is made available so that researchers are able to verify that the script only captured relevant tweets. Deletion of these tweets by the Twitter Safety team can be considered a safe action.
3. The number of unique accounts mentioned on user account lists in tweets that met the script's criteria was XXX. This list can be found in this repository in a file named tofollow.json. The list contains screen_names, since the accounts were not queried via the API for their user id_str values. Since any user can mention any screen_name in a tweet, without the consent of the screen_name's owner, it would not be safe to automate actions on this list of accounts. However, they are provided since it is assumed that a majority of the accounts are willing participants in the follow-back network, and thus further analysis of these accounts could prove useful.

The accounts involved in this network were observed to share COVID-related disinformation, anti-vax conspiracy theories, racist content, QAnon-related content, and extremist material. By-and-large the accounts are high-volume (publish hundreds of tweets per day) and have follower and following counts in the tens of thousands. Account creation dates vary, and no further analysis was performed on them.

Some of the identified accounts have been actively participating in this behaviour for several years. For instance, the script discovered the PaulMer53 account, almost identical to a PaulMer52 account observed participating in pro-Brexit content amplification during the 2019 UK General election.

![](images/PaulMer53.png)
![](images/PaulMer52.png)

Also observed were accounts that auto-delete tweets at a rapid rate. For instance, according to Twitter's UI, this account has published 47.6k tweets. The script was ony able to obtain 175 tweets from the account, meaning that the rest were deleted, likely by automation.

![](images/LindaNTx.png)

# Conclusion
The accounts identified during this research represent a very small subset of inauthentic sock puppets whose purpose is to amplify extremist and divisive content on Twitter. The actions of this group of users are a detriment to society and are contributing to major societal problems, such as the January 6th attack on the US Capitol building and riots related to the refusal of the COVID-19 vaccine. The group's high-volume activity directly contributes to the amplification of content designed to cause societal divide, spread harmful disinformation, and gravitate people towards extremist viewpoints. The mechanisms they use are not new, and many of the accounts identified in this research have likely been participating in this activity for years. The data provided in this repository represents a starting point for analysis of this group as a whole. The contributors to this research hope that Twitter's Safety team perform such an analysis and take appropriate actions to curb these mechanisms once and for all.
