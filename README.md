# Electricity-Price-Comparing

Electricity Price Comparing (EPC) is a final project of mine for the Building AI course. 

## Summary

EPC compares electricity contracts offered by Finnish providers, such as Fortum and Helen, to determine the most suitable contract based on the user's preferences and requirements. The contract details are readily available on the providers' websites, allowing us to calculate the best provider by assigning points to different factors, including price, contract duration, and personal electricity consumption. 

## Background

The idea behind my project is to simplify the process of selecting an electricity contract and provider. I'm aware that there are already numerous websites that display various contracts, but I want to introduce a unique feature. This feature would allow users to consider their personal factors, such as the size of their apartment, the number of residents, and their location.

This idea came to me about a month ago when I had to change my own electricity contract. It was a nightmare trying to determine the best option for my needs. Additionally, the websites and apps that provide spot-electricity prices are often outdated. I'm not an expert on this topic, but I would say the leraning type would be reinforcement  learning because the code would maximize the points, giving the user the best contract for their needs. 

## How is it used?

The code will incorporate various datasets from different electricity providers, and these datasets will update as the providers modify their contracts. Users can select their preferred contract type, such as spot-price or fixed-price, with options for different durations (e.g., 6 months, 12 months). Users can also input unique features, as mentioned earlier. Using this information, the algorithm will identify the optimal provider and contract for each user.

<img src="https://github.com/Agetso/Electricity-Price-Comparing/assets/149581762/3f3dc2f9-b3f5-41a4-abd9-b31f0bca2e3f" width="1000">

Here's a simple part of code on how the algorythm would work: 

https://github.com/Agetso/Electricity-Price-Comparing/blob/main/import%20pandas%20as%20pd.py

## Data sources and AI methods

Electricity prices from various providers are easily accessible on their websites. This data can be imported into Python and utilized by the functions that calculate the best provider. These functions can adapt to changes in the data, continually identifying the most optimal contract based on prior knowledge.

Here are some finnish electricity providers and their contracts:
[Fotrum API](https://www.fortum.fi/en/for-households/electricity/contracts)
[Helen API](https://www.helen.fi/en/electricity/electricity-products-and-prices)
[Väre API](https://vare.fi/sahkosopimus/)

## Challenges

How can the code chenge as the real time contract prices and electricity prices change? In other words, how can the algorythm update the data in the code real time. 

## What next?

The next step in EPC involves forecasting future electricity prices, such as spot-electricity contracts, and determining the optimal times for electricity usage. This forecasting tool can also have broader applications, including stock price forecasting for future projects.

## Acknowledgments

People, their work and different sources involved in the EPC project will be mentioned here.
