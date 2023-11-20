# Election-Dataset-Analysis-Project-Python

## Introduction
This project analyzes a sample election dataset using Python and the Pandas library. The dataset includes voter information such as voter ID, age, gender, party affiliation, and whether they voted.

## Data Cleaning
The "Data Cleaning" is displays a Handle missing values by filling NaN values with the mean age.

## Voter Turnout
The "Voter Turnout" is a Calculate and display the voter turnout percentage.

## Demographics Breakdown
The "Demographics Breakdown" is a Display a breakdown of voters by gender.

## Party-wise Results
The "Party-wise Results" is a Display the results by party.

## Key Statistics
The "Key Statistics" is a Generate and display key statistics about the dataset.

## Voter Insights
The "Voter Insights" is a Generate and display insights from the dataset.


## App Code
import pandas as pd
# Sample election dataset
data = {
    'Voter_ID': [1, 2, 3, 4, 5],
    'Age': [30, 45, 35, None, 28],
    'Gender': ['M', 'F', 'M', 'F', 'M'],
    'Party': ['A', 'B', 'A', 'C', 'B'],
    'Voted': [1, 1, 0, 1, 0]
}

# Create a DataFrame
election_df = pd.DataFrame(data)

# Print the initial dataset
print("Initial Dataset:")
print(election_df)

# Handle missing values by filling NaN values with appropriate defaults
election_df['Age'].fillna(election_df['Age'].mean(), inplace=True)

# Function to calculate voter turnout
def calculate_voter_turnout(df):
    total_voters = len(df)
    voted_count = df['Voted'].sum()
    turnout_percentage = (voted_count / total_voters) * 100
    return turnout_percentage

# Function to generate demographics breakdown
def demographics_breakdown(df):
    demographics = df.groupby('Gender')['Voter_ID'].count()
    return demographics

# Function to get party-wise results
def party_wise_results(df):
    party_results = df.groupby('Party')['Voted'].sum()
    return party_results
    # Calculate voter turnout
voter_turnout = calculate_voter_turnout(election_df)
print("\nVoter Turnout: {:.2f}%".format(voter_turnout))

# Get demographics breakdown
demographics = demographics_breakdown(election_df)
print("\nDemographics Breakdown:")
print(demographics)

# Get party-wise results
party_results = party_wise_results(election_df)
print("\nParty-wise Results:")
print(party_results)
# Function to generate key statistics
def generate_statistics(election_df):
    statistics = {
        'Total Voters': len(election_df),
        'Average Age': election_df['Age'].mean(),
        'Male Voters': len(election_df[election_df['Gender'] == 'M']),
        'Female Voters': len(election_df[election_df['Gender'] == 'F']),
        'Oldest Voter Age': election_df['Age'].max(),
        'Youngest Voter Age': election_df['Age'].min(),
    }
    return statistics

# Function to generate insights
def generate_insights(election_df):
    insights = {
        'Most Common Gender': election_df['Gender'].mode()[0],
        'Most Common Party': election_df['Party'].mode()[0],
 
    }
    return insights

# Example usage:
key_statistics = generate_statistics(election_df)
print("Key Statistics:")
print(key_statistics)

voter_insights = generate_insights(election_df)
print("\nVoter Insights:")
print(voter_insights)
