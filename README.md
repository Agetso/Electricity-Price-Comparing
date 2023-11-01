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

Check out the code for EPC file for some basics on how would the algorythm work. The output should look like this:

#mockup for EPC
import pandas as pd
import matplotlib.pyplot as plt

#Contract data of different providers
contract_data = [
    {"provider": "Fortum", "price": 0.11, "duration": 12, "production_type": 0, "max_consumption": 1000},
    {"provider": "Helen", "price": 0.10, "duration": 6, "production_type": 1, "max_consumption": 800},
    {"provider": "Väre", "price": 0.09, "duration": 24, "production_type": 2, "max_consumption": 750}
]

#User preferences
user_preferences = {
    "max_price": 0.09,
    "duration": 12,
    "production_type": 1,
    "max_consumption": 900
}

#Function to calculate points
def calculate_points(contract, user_prefs):
    points = 0

    if contract["price"] <= user_prefs["max_price"]:
        points += 1

    if contract["duration"] >= user_prefs["duration"]:
        points += 1

    if contract["production_type"] == user_prefs["production_type"]:
        points += 1
    else:
        points -= 1

    if contract["max_consumption"] <= user_prefs["max_consumption"]:
        points += 1

    return points

#Find the best contract
def find_best_contract(contracts, user_prefs):
    best_contract = None
    best_points = -1

    for contract in contracts:
        points = calculate_points(contract, user_prefs)
        if points > best_points:
            best_contract = contract
            best_points = points

    return best_contract

#Get the best contract
best_contract = find_best_contract(contract_data, user_preferences)

#Create a dataframe for contract data
df = pd.DataFrame(contract_data)

#Display the contract data
print("Contract Data:")
print(df)

#Display the best provider
print("\nBest Provider:")
print(f"Provider: {best_contract['provider']}, Price: {best_contract['price']}, Duration: {best_contract['duration']} months, Production Type: {best_contract['production_type']}, Max Consumption: {best_contract['max_consumption']} kW")

#Plot the contract data
plt.figure(figsize=(10, 6))
plt.title("Electricity Contract Data")
plt.bar(df["provider"], df["price"], color="lightblue")
plt.xlabel("Provider")
plt.ylabel("Price (cents/kWh)")
plt.xticks(rotation=15)
plt.tight_layout()

#Show the plot
plt.show()


![image](https://github.com/Agetso/Electricity-Price-Comparing/assets/149581762/2e0a6407-0f74-41c5-bc3a-f1f511cccf20)


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
