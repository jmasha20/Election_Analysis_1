# Analysis of Election Audit

## Overview of Election Audit
A Colorado Board of Elections wants confirmation and analysis of a recent local congressional election. The following list of tasks was performed for this analysis. 

1. Calculate the total number of votes cast.
2. Get a complete list of candidates who received votes.
3. Calculate the total number of votes each candidate received.
4. Calculate the percentage of votes each candidate won
5. Determine the winner of the election based on popular vote.

## Resources
-Data Source: election_results.csv
-Software: Python 3.7.6, Visual Studio Code, 1.52.0

## Election-Audit Results

* Total Votes Cast in Congressional Election: 369,711

* **Number of votes and the percentage of total votes for each county in the precinct:

    * Jefferson: 10.5% (38,855)
    * Denver: 82.8% (306,055)
    * Arapahoe: 6.7% (24,801)

* **Largest County Vote Turnout: Denver

* **Number of votes and the percentage of the total votes each candidate received.

    * Charles Casper Stockham: 23.0% (85,213)
    * Diana DeGette: 73.8% (272,892)
    * Raymon Anthony Doane: 3.1% (11,606)

* **Winner: Diana DeGette
* Winning Vote Count: 272,892
* Winning Percentage: 73.8%

## Election-Audit Summary
The analysis performed confirms the votes and winner by county in the congressional election. The election commission should refer to the code modifications to the original code for future audits, to include the county analysis. 

Examples code modifications:

##### Create a county list and county votes dictionary.

counties_options = []
counties_votes = {}

##### Write an if statement that checks that the
        # county does not match any existing county in the county list.
        if county_name not in counties_options:

            # Add the existing county to the list of counties.
            counties_options.append(county_name)

            # Begin tracking the county's vote count.
            counties_votes[county_name] = 0

        # Add a vote to that county's vote count.
        counties_votes[county_name] += 1

##### Write a for loop to get the county from the county dictionary.
    for counties_option in counties_options:
        # Retrieve the county vote count.
        votes = counties_votes[counties_option]
        # Calculate the percentage of votes for the county.
        vote_percentage = float(votes) / float(total_votes) * 100
        counties_results = (
            f"{counties_option}: {vote_percentage:.1f}% ({votes:,})\n")
            
         # Print the county results to the terminal.
        print(counties_results)
         # Save the county votes to a text file.
        txt_file.write("\n" + counties_results)
       
         # Write an if statement to determine the winning county and get its vote count.
        if (votes > winning_county_count) and (vote_percentage > winning_percentage):
            winning_county = counties_option
            winning_county_count = votes
            winning_percentage = vote_percentage

[See complete code here](https://github.com/jmasha20/Election_Analysis_1/blob/main/analysis/election_results.txt)
