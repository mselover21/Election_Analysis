# Election_Analysis_Challenge

##Overview
The Challenge this week had me complete an election analysis but take it a few steps further.
1. Calculate the total number of votes in the election.
2. Get the number of votes for each county in the precinct and calculate percentage totals for each county.
3. Find the county with the largest turnout.
4. Create a breakdown of number of votes and percentage of votes for each candidate.
5. Provide who which candidate won the elction, their vote count, and their percentage of the total votes.

###Resources
- Data Source: election_results.csv
- Software: Python 3.7.6

####Summary
After analyzing the data the results of the election are as follows
- There were 369,711 total votes cast
  - Within the starter code to calculate total votes you first initialize a counter (vote_counter = 0)
  - Then you create a for loop to to count through all the rows of data and count the number of votes
    - for row in reader:
       total_votes = total_votes +1
- There are 3 Counties Jefferson, Denver, Arapahoe.
  - First I had to create a list and dictionary for counties and county votes.
    - county_list[] 
    - county_votes{}
  - Next I needed to create variables to track the largest county and county voter turnout.
    - largest_county_turnout =""
    - largest_county_turnout_count = 0
    - largest county percentage = 0
  - I then needed to get each county name from each row.
    - county name is in the second column so I created a variable county_name = row[1]
  - Next I created conditionals within the for loop that would check the rows of a data for
    - Counties that are not in the list and add them
      - if county_name not in county_list:
          - county_list.append(county_name)
    - Begin tracking each county's vote
          - county_votes[county_name] = 0
    - Create a vote count for each county's votes
      - county_votes[county_name] += 1
  - I now needed to write a for loop to get each county's vote count and percentage of vote
    - for county in county list:
   - Retrieve county vote count
      - county_vote = county_votes.get(county)
   - Calculate percentage of votes in each county
      - county_vote_percentage = float(county_vote) / float(total_votes) * 100
   - Print the results to the terminal
      - county_results = f"{county}: {county_vote_percentage}:.1f}% ({county_vote:,})\n"
   - Here I had to add a print syntax to make sure that county results would print in the terminal
      - print(county_results)
   - Next I wrote an if statement to determine the winning county and get its vote count.
      - if (county_vote > largest_county_turnout_count) and (county_vote_percentage > largest_county_percentage):
        - largest_county_turnout_count = county_vote
        - largest_county_percentage = county_vote_percentage
        - largest_county_turnout = county
  - Now I was fianally ready to print the winning county results to the terminal and write them to the .txt file.
    - winning_county_print = (
       - f"-----------------------------\n"
       - f"Largest County Turnout: {largest_county_turnout}\n"
       - f"-----------------------------\n"
       - )
    - txt_file.write(winning_county_print)
- The county results are:
  - Denver county was the largest county with the highest vote count and the highest percentage.
    - Jefferson: 10.5% (38,855)
    - Denver: 82.8% (306,055)
    - Arapahoe: 6.7% (24,801)
  - Diana Degette won the election with a winning vote count of 272,892 and a winning percentage of 73.8%
![Election_Results_Printed_Terminal.png](https://github.com/mselover21/Election_Analysis/blob/main/Election_Results_Printed_Terminal.PNG)
 
#####Challenge Summary
In summary the script that has been written almost all elections and can help campaigns to better spend their resources during election seasons. There are a couple things that may be needed to analyze elections that are national. In that case I would add modifications to the script by adding another for loop to differentiate between not just counties but states as well. Depending on the data you are provided you may also need to change specific lines of code. For example, if you have a data set where the county and candidate are switched positions in the index you will need to change the code to tell the computer to search index 1 instead of 2 for the candidate name. All in all I found this assignment to be very challenging and educational. I feel that I have broad understanding of how python works and look forward to learning better ways to utilize it as a tool.

