# Election_Analysis

## Project Overview

The goal of this analysis was to use python to calculate the election results from a local congressional election.

We were to provide the following:
  1. The total votes cast in the election.
  2. The total number of votes from each county as well as the count and percentage of votes from that county.
  3. The county with the largest voter turnout. 
  4. The candidates names, the percentage of votes they received as well as the total count of votes they received.
  6. Calculate the winner of the election and display their total winning vote count and winning percentage
  6. Export the information above to a text file that can be provided to our managers

## Resources

- Data Source: election_results.csv
- Software: Spyder 4.1.4

## Summary

We were able to get these results by first pulling out a list of candidate names, then a list of county names from the source `election_results.csv`
```
if candidate_name not in candidate_options:
  candidate_options.append(candidate_name)
```
and
```
if county_name not in county_list: 
  county_list.append(county_name)
```
Then used those in loops to pull out the information associated with each name. ie. we set the number of votes in each county to 0 then added 1 to it each time the line contained the county name:
```
county_votes[county_name] = 0
  county_votes[county_name] += 1
```

There were also calculations to give us the percentage of votes per county and percent of votes per candidate:
Votes per county: `cvote_percentage = float(cvotes) / float(total_votes) * 100`
Voter per candidate: `vote_percentage = float(votes) / float(total_votes) * 100`

We also needed to calculate the overall winner which was done by comparing the number of votes per candidate and only returning the candidate with the most, along with their total vote count and percentage of votes they received:
```
if (votes > winning_count) and (vote_percentage > winning_percentage):
  winning_count = votes
  winning_candidate = candidate_name
  winning_percentage = vote_percentage
```

We did something similar to get the county that had the largest percentage of votes:
```
if (cvotes > county_count):
  county_count = cvotes
  winning_county = county_name
```
Finally for each of these results we needed to save them to a text file using the `txt.file.write()` command.

## Results

The results that we received in our text file looked like this: 

![1](https://github.com/ccastanette/Election_Analysis/blob/master/Analysis/election_results.txt)

This code can be used with any election results that are stored in the same format and will be very useful in other elections.
