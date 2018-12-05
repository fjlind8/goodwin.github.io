# The GoodWin Project

Welcome to the GoodWin Project github repository! This repository contains all the files that fuel our [website](https://fjlind8.github.io/) as well as the code used to create our [time series model](https://github.com/fjlind8/fjlind8.github.io/blob/master/Data%20Transformation%20and%20Time%20Series%20Model.Rmd) to forecast species populations.

## Storytelling User Guide

This section will outline the visualizations in the *Explore* section and talk through some insights we can get from them.

### Model Population Forecast

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/model%20population%20forecasts_blue%20whale.PNG "Model Population Forecast - Blue Whale")

All of the visualizations are defaulted to show information for the Blue Whale, as shown above. Currently, we are seeing species for all countries on the map and in the table at the top. The bottom line graph shows the annual total number of individual blue whales over time (the thin green line) as well as the forecast (the thick green line). There are also confidence intervals for the forecast (the thick blue lines). The light blue line is the 80% confidence interval and the dark blue line is the 90% confidence interval. The confidence interval gives us a range of values that it is 80% (or 90%) probable that the true value will be contained in. This gives us an idea of how much certainty we should have in the calculated forecast.

We can see that the population for blue whales has been steadily declining since 1992 with the most recent numbers approaching 0.

As you can see, our forecast projects the population to keep declining, even reaching into negative numbers. Now, we know that it is impossible to have a negative number for a species population. We considered defaulting these numbers to 0, but we did not want to lose the true shape of the forecast line, so we allow the model to forecast negative numbers so we can better see how quickly an decrease is projected to happen.

Let's look at some other species. On the top right map, select Antartica. Then, select the Antartic fur seal in the table. This gives the population and forecast over time.

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/model%20population%20forecasts_antartic%20fur%20seal.PNG "Model Population Forecast - Antartic Fur Seal")

We can see that our model is forecasting this species to steadily increase over time. There are a few things to note here.

First, notice that the Units measure to the left of the line graph is different than our previous example. There are a very wide variety of ways that researchers use to measure populations, often there are several kinds of measurements for the same animal! This was a difficult obstacle in our analysis. Due to the volume of data and time constraints to deliver this solution, we combined as many similar labels as we could (like combining measures such as "Number of seals" and "Individuals") and used whichever measure had the most data in the model. 

In this model, the forecast has a pretty tight confidence interval which widens the further that the forecast goes into the future. This widening over time is very typical. For example, given this data: if you were trying to estimate the population, you would probably be more confident in your guess for the next year than you might for 10 years from now.

Now, let's examine the fin whale.

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/model%20population%20forecasts_fin%20whale.PNG "Model Population Forecast - Fin Whale")

This population line graph is a little less consistent than the previous two. There are more spikes and plateaus in the historical population data. Because of this, the forecast isn't very dynamic. It essentially looks like a flat line that doesn't change very much or at all in the future. Unfortunately, this means that the time series model could not really detect a trend, so what essentially happens is it ends up just averaging these values (with the most recent values being weighted a bit more than values more into the past). You can see this in the graph because the forecast falls between the lowest and highest historical values. This also results in a very large confidence interval, which means that we have a lot more uncertainty with this forecast.


### Species in Decline

The Species in Decline visualization only lists the species that have an ending forecast value that was less than the first value that was forecasted. It is also defaulted to show the blue whale.

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/species%20in%20decline%20_blue%20whale.PNG "Species in Decline - Blue Whale")

We can see a line graph almost identical to the previous dashboard, but this one has IUCN assessments marked in text over the line. So, in this example, we can see that the blue whale was first assessed in 1988 as Endangered and has been assessed 3 more times with the same outcome.

If we look at the table below, it outlines threats that have been identified by IUCN for this species, both ongoing threats and past threats. We can see the blue whale has one identified future threat, habitat shifting and alteration, as well as two others that have been marked as past and unlikely to return.

With this, we know that the blue whale is an endangered species that is projected to keep declining and there are threats that have been identified. Although this seems like a bad situation, there are some good things to note here: we have a good history of data for this animal, and organizations are aware of its status and the threats to this species' existence. Unfortunately, this is not always the case. Not every animal has been assessed by IUCN and many animals that have been assessed might not have threats identified. 

Let's look at another animal. Select the short-eared owl from the table at the top.

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/species%20in%20decline%20_short%20eared%20owl.PNG "Species in Decline - Short-eared Owl")

Although this species has a lot of ups and downs in the population (annual index of abundance), it appears to be steadily declining over time. The forecast carries this pattern as well. This species also has a long list of threats that could be contributing to why it is declining. Although this might initially appear alarming, the IUCN has assessed this species as being of Least Concern. There are a few things we should keep in mind. 

Firstly, we don't know if the source for the population data we are using in the model is the only source to measure population. As explained above, if there are many different measurements for a species in our Living Planet Index population dataset, we can only use one in the model. It's possible that there are multiple units of measurements that could not be combined that are not being considered by the model. It's also possible that there are more sources of population data that we do not have access to that go into the IUCN's considerations. The IUCN uses many sources and a rigorous process to make these assessments. These are important things to consider when exploring this data. This also highlights the greater need for bigger and more connected sources of wildlife data.


Let's go through one more example, the Red-breasted goose.

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/species%20in%20decline%20_red%20breasted%20goose.PNG "Species in Decline - Red-breasted goose")

This species experienced a drastic decline after 1992, which is probably why it was labelled by IUCN as only "Threatened" before 1992 and changed to "Vulnerable" and eventually "Endangered post-1992. Although the most recent IUCN assessment bumped it back up to only "Vulnerable," the model still projects a slow decline in the future. We can also see there are a long list of threats identified by IUCN. 

When considering threatened, vulnerable, or endangered species we often wondered if there was a way to measure awareness around this. This is a very challenging thing to measure, but we attempted to try to get an idea if anyone was asking questions about a species by collected Google Trends data by gathering data (if any) on searches containing the common names of the species in our dataset from 2014 until present. 

The results for this are in our third visualization, Google Trends Popularity. The list of species in this dashboard is shorter because we chose not to include species that had no searches. We think this highlights the need for more tools to promote this kind of exploration and awareness for every audience, not just researchers. If you search for the Red-breasted goose, unfortunately you will not see it in the list. 

However, we can look at some of the other species we have covered in this walkthrough. Let's look at the blue whale first.

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/google%20trends%20popularity_blue%20whale.PNG "Google Trends Popularity - Blue Whale")

From this visualization, we can see in the table at the top that the blue whale is currently classified as endangered. There are two maps below--the one in the bottom left shows the countries that the blue whale has populations in. The one to the right shows a heat map of Google Trend searches by country. So, the darker countries search Google for blue whale more than the lightly colored countries. We can see a high concentration of countries around Bangladesh, India, and Pakistan.


Let's look at the Antartic fur seal. You can select it from the table at the top.

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/google%20trends%20popularity_antartic%20fur%20seal.PNG "Google Trends Popularity - Antartic fur seal")

Although the Antartic fur seal has populations in several countries, it gets pretty much all of its traffic on Google from Australia.

You can also filter the results to choose from in the table by selecting either IUCN classification or animal class. Let's look at the Short-eared owl (which was one of our declining species examples) by selecting "Aves" from the Class dropdown, and then selecting Short-earted owl in the table.

![alt text](https://github.com/fjlind8/fjlind8.github.io/blob/master/img/google%20trends%20popularity_short%20eared%20owl.PNG "Google Trends Popularity - Short-eared owl")

We can see a wide variety of countries reporting populations for the Short-eared owl, but most of the searches are coming from the United States.


## Closing Thoughts
We hope that this walkthrough will help educate others on how to use our project, encourage exploration of conservation and biodiversity data and topics, and inspire action. Thank you!
