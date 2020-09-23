+++
title = "My HackMIT 2020 Experience"
description = "Our Covid-19 prediction project for HackMIT 2020"
date = 	2020-09-23T16:40:00+00:00

[taxonomies]
categories = ["Blog"]
tags = ["HackMIT", "Python", "Dev"]

[extra]
comments = true
+++

# My HackMIT 2020 Experience

## Intro:

So this past weekend, I participated in HackMIT, I was part of a team which consisted of Sam and I, Sam's a friend from
Imperial. We went into the hackathon thinking we should use the Goldman Sachs' API as it gave us access to a vast
amount of data which could easily be analysed using their own API. Our original project's concept was to use Phone 
Triage data as a predictor of localised outbreaks.

## Issues:

Some issues that we came across were:

- The datasets did not match up with locations, as the API's used different levels of localisation
- The data had overlapping bounds when trying to match the data between the government data, and the phone triage data
- We had absolutely no idea how the Marquee API's correlation function worked
- Data Visualisation boundaries -- with Plotly

## Resolution:

### Dataset locations
In order to solve the mismatching of location data, we had to investigate the location data we received from the API, 
both the Government API and the Marquee API provided locations using the
[ONS GSS](https://en.wikipedia.org/wiki/ONS_coding_system#Current_GSS_coding_system) system, this resulted in us trying
various avenues to link both sets together, with finding no reasonable solution other than matching by using 
[this api](https://findthatpostcode.uk/#api), we ended up using the longitude and latitude of each location to find 
distances between each one and generate a link between API locations.

### Overlapping Bounds
Due to the previous issue, we found that some Government locations had double links to the NHS locations, and this 
resulted in a strange error in the stacktrace. This error occurred merely a few hours before the deadline, and so we 
tried many StackOverflow solutions to a somewhat generic error message that stated there was a duplicate axis, to which
I had absolutely no clue what had happened until I noticed that the loop fulfilled about ~90 iterations before crashing.
This made me come to the realisation that something must have been doubly-linked. As we had close to minutes left, 
I decided instead of concatenating the overlapping data, to just put a `try` and `except` block to ignore the 
overlapping bounds.

### Marquee's Correlation function
My limited knowledge in time series analysis was apparent in this project, as I had absolutely no clue how to correlate 
two time series over many lags and find the optimal delay between the two for the maximal correlation. The Marquee API's
correlation function produced another time series, which I believe contained values ranging from -1 to 1, however at 
times produced erroneous `inf` results. With my lack of statistical knowledge I just took the naive mean of the function
over iterations that varied the window parameter, this produced a very small correlation between the two time series, 
ranging from 0.3-0.6 with an average lag of 21 days. My hypothesis as to why the correlation is so low, is due to noise
in the data, to solve this in the future, I would implement some data-smoothing to both time series before correlating 
them.

### Data Visualisation boundaries
Towards the tail end of the hackathon we decided to try to implement some data visualisation, hopefully two choropleth 
maps, that could show the location based density of both phone triage calls and confirmed cases, with a time slider,
to show how localised outbreaks could have potentially been predicted from phone triage call data. Unfortunately, as 
we thought of this feature nearing the closing of the hackathon, we were unable to implement it, this came down to 
Plotly not supporting UK counties by default, this would have been quite easy to implement using GeoJSON data provided 
by the [findthatpostcode API]((https://findthatpostcode.uk/#api)), which we had used earlier, as Plotly allows 
boundaries defined by GeoJSONs.

## Conclusion

All in all, this hackathon has been fun, albeit very different to most hackathons that I've been to, as this one is the 
first virtual hack I've participated in. I found the Goldman Sachs team extremely helpful at explaining the Marquee API, 
and the Marquee API to be extremely well-documented. I had a blast participating in the hackathon, and I can't wait for 
the next one. Here's a [link](https://github.com/SamtheSaint/HackMIT2020) to our project on Github, if you want to 
check it out!
