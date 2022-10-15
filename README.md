#cv

# Database Table Documentation for Voting Buck
## v1: Moneet Tiwana – October 11, 2022

### Anchor tables for units
 
**Unit (unit)**<br> 
This table assigns a Voting Buck ID to a new item that is added to the database that would be classified as one of the following:
* Politician
* University
* Corporation

### Politician Tables

Politician
Constant characteristics of politicians in unit and career tbl

Career (career)
This table outlines general information about politicians’ careers including the career field as well as the start and end dates for each career for each politician. The Career table references the Politician table.
 
Committee 
The Politician table references this table to identify committee membership for each politician.
 
Committee Membership (committee_membership)
This table highlights the committees that each politician is involved in as well as general committee information. This can include information such as time served within each committee and the rank held by each politician within the committee as well. The Committee Membership table references the Politician table to specify each politician.

Majority_minority 
which party is in power in which chamber in which congress: matters for power-score

Leadership_spell   
there are about 7 leadership roles per party per chamber, ie around 28ish total. Important determinant of power-rank!

Committee-tbl
thomas_id identifies each of around 40 total committees in congress


Ideology Score (ideology_score)
This table highlights how far left, right, or center a politician may be based on the Voting Buck ideology scale. This table references the Politician table to assign each politician with an ideology score.


Politician Education (politician_education)
This table highlights the education of politicians by referencing both the University and Politician tables. The universities and colleges attended by each politician will be present in this table.
 
Power Ranking (power_ranking)
The Power Ranking table ranks each politician based on their position within the government. This table considers the committees the politician is involved in as well as the ranks within each party, Republican or Democrat. The Power Ranking table references the Politician table to specify each politician.
 
Sentiment Analysis (sentiment_analysis)
This table is populated based on Twitter sentiment information gathered through a Twitter sentiment API collected on a specified date. Further information regarding Twitter presence including retweets is collected while referencing the Politician table to specify each politician and their respective Twitter presence.
 
*** ***  CORPORATION

Corporation (corporation)
This table highlights general information about a certain corporation including location, revenue, number of employees, among other identifying information. This information is used in donation_aggreg_by_org to identify donations to politician committees made by these corporations.

*** *** Contribution/Donation Flows 

cmte
This table outlines committee information and is important for tracking donations from both individuals and organizations. 
All donation and donation_aggreg tables characterize money flows to and from committees in cmte-tbl

1 of 3)
Individual Donation (indiv_donation)
The Individual Donation table outlines the amount of the donation and is also given a unique ID to identify the transaction. The important information to note here is the committee that the donation is made to. Further information about committees can be found in the cmte-tbl.
Donation by Organization (donation_aggreg_by_org)
The Donation by Organization table outlines the amount of the donation and is also given a unique ID to identify the transaction. The important information to note here is the committee that the donation is made to. It aggregates the sender of money from ‘indiv_donation’ tbl. 
 
(Donation_aggreg_by_recip)
aggregated the recipient of money from ‘indiv_donation’ tbl. This one is only for total receipts by 2-year window

2 of 3)
Pac_to_candidate 
committee to candidate-committee transfers, subsumed now in more aggregate ‘donation_aggreg_by_cmte’

3 of 3)
Pac_to_pac	
committee to committee transfers, also subsumed now in more aggregate ‘donation_aggreg_by_cmte’

Donation by Committee (donation_aggreg_by_cmte)
The Donation by Committee table outlines the amount of the donation and is also given a unique ID to identify the transaction. The important information to note here is the committee that the donation is made to. Further information about committees can be found in the Committee table.
 
*** ***  Lobbyists 





Lobbyist_registration 
→ 1.1m quarterly lobby filings (=contracts)between registrants (lobby-firms) and clients (regular firms)

Lobbyists_byfiling 
→ IDs of lobbyists associated with a filing

 Issues_byfiling 
→ issues-codes associated with a filing

Issues_lobbying 
→ issue-codes to issue-string-descriptions (79 total)

Lobbyist_contributions
→ contributions made by lobbyists (acting for their registrant companies) to politicians

 *** ***  UNIVERSITIES

University (university)
This table simply outlines information regarding a university or college in the database. Some of the important information outlined in this table include:
Name
Location
Rank
Date of foundation
Public or Private
Number of enrolled students
Website
American or Foreign
 
University Voters (university_voters)
This table outlines information about registered faculty voters from each university 
