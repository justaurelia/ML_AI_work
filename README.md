# Project Name

Practical application: Will the customer accept the coupon ?

## Context

Imagine driving through town and a coupon is delivered to your cell phone for a restaraunt near where you are driving. Would you accept that coupon and take a short detour to the restaraunt? Would you accept the coupon but use it on a sunbsequent trip? Would you ignore the coupon entirely? What if the coupon was for a bar instead of a restaraunt? What about a coffee house? Would you accept a bar coupon with a minor passenger in the car? What about if it was just you and your partner in the car? Would weather impact the rate of acceptance? What about the time of day?

Obviously, proximity to the business is a factor on whether the coupon is delivered to the driver or not, but what are the factors that determine whether a driver accepts the coupon once it is delivered to them? How would you determine whether a driver is likely to accept a coupon?

## Overview

The goal of this project is to use what you know about visualizations and probability distributions to distinguish between customers who accepted a driving coupon versus those that did not.

## Data

This data comes to us from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios, including the destination, current time, weather, passenger, etc., and then asks people whether they will accept the coupon if they are the driver. Answers given that the users will drive there “right away” or “later before the coupon expires” are labeled as “Y = 1”, and answers “no, I do not want the coupon” are labeled as “Y = 0”. There are five different types of coupons—less expensive restaurants (under $20), coffee houses, carry out and take away, bars, and more expensive restaurants ($20–$50).

### Data Description
Keep in mind that these values mentioned below are average values.

The attributes of this data set include:
1. User attributes
    -  Gender: male, female
    -  Age: below 21, 21 to 25, 26 to 30, etc.
    -  Marital Status: single, married partner, unmarried partner, or widowed
    -  Number of children: 0, 1, or more than 1
    -  Education: high school, bachelors degree, associates degree, or graduate degree
    -  Occupation: architecture & engineering, business & financial, etc.
    -  Annual income: less than \\$12500, \\$12500 - \\$24999, \\$25000 - \\$37499, etc.
    -  Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    -  Number of times that he/she buys takeaway food: 0, less than 1, 1 to 3, 4 to 8 or greater
    than 8
    -  Number of times that he/she goes to a coffee house: 0, less than 1, 1 to 3, 4 to 8 or
    greater than 8
    -  Number of times that he/she eats at a restaurant with average expense less than \\$20 per
    person: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    -  Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
    

2. Contextual attributes
    - Driving destination: home, work, or no urgent destination
    - Location of user, coupon and destination: we provide a map to show the geographical
    location of the user, destination, and the venue, and we mark the distance between each
    two places with time of driving. The user can see whether the venue is in the same
    direction as the destination.
    - Weather: sunny, rainy, or snowy
    - Temperature: 30F, 55F, or 80F
    - Time: 10AM, 2PM, or 6PM
    - Passenger: alone, partner, kid(s), or friend(s)


3. Coupon attributes
    - time before it expires: 2 hours or one day

## Summary of Findings

This application focus on 2 types of coupons, here are some observations and findings : 
### 1- Bar coupon analysis
The global acceptance rate of the bar coupon is 41 %.
Drivers who accepts Bar coupons are most likely the ones who used to go often to bars (more than 4 times a month).
Some criteria and habits increase the acceptance rate such as having passengers (except kids), being young (<30 years old), marital_status (not being widowed)
Others criteria such as habits on frequency to go to cheap restaurant and income doesn't impact much the acceptance rate.

### 2- Coffee House coupon analysis
The global acceptance rate of the coffee house coupon is 50 %.
Contextually,
- drivers with passengers but not kid(s) have a good acceptance rate
- commit during late morning have the best acceptance rate
- drivers going to a no urgent place have the best acceptance rate
- coupons which expire in 1 day have a better acceptance rate than 2 hours coupon
- a sunny day give an equal chance for the coupon to be accepted. But a rainy day as a better chance to be accepted compared to a snowy day.
On the user profile:
- There is no clear pattern about customers regarding the gender, marital status or children criteria
- Divorced or single people have a slight better acceptance rate than others
- Younger drivers are most likely to accept the coupon rather than older drivers
- Students, Unemployed and Computer & Mathematical got the most of coupons and Students accepted most of the time the coupons
- Drivers working in healthcare or building accepted a lot the coupons too
Concerning the user habits:
- a driver who goes often to a coffee house (more than once a month) has a better acceptance rate
- a driver who goes fewer to the other places has a slight better acceptance rate but it's not significant

## Next steps and recommendations
One of the possible target with a good acceptance rate (84 %) for the coffee house coupon could be :
- young drivers (under 30 years old)
- drivers who use to go at least once a month in a coffee house
- drivers with passengers other than kid(s)
- drivers who drive to a No Urgent Place
- at 10AM
- with a coupon which expire in 1 day 

It would be great to do the same analysis for the other types of coupons.
And also compare the acceptance rate for a specific target like it's done for Coffee House with the different types of coupons and see if a target is more likely to accept any kind of coupons.

## Notebooks

- [Jupyter Notebook](./main_notebook.ipynb): A detailed exploration and analysis of the data.
