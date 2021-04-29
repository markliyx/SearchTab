# SearchTab
A functional search tab interacting with RestDB API

Functionality: a search tab given search parameters inputed by user, output a table of merchants. From the search tab, the program connects to RestDB's API and quereies merchants with similar ID, tax ID, and merchant names as the search input. 

Define Similar as either exactly the same or contained by the element in the merchant field. Considering space complexity, I did not choose to use Jaccard similarity to find the non-exact or contained searches. If use Jaccard similarity, I have to querie the entire dataset of 1 million merchants, which can take a lot of space. 

Note: I created a emulating database to test my code. The querie prefix in the code is "https://testing-0093.restdb.io/rest/stores". For the sake of the assignment, replace the prefix by https://api.koibanx.com/stores is sufficient. 

Features: 
Search - inputing in the search bar and click search will return a table of "similar" merchants.
Filter active/ inactive - after "similar" merchants are returned, the user can click on "Active Merchants", "Inactive Merchants", or "Both" button to filter out by the activity of the merchants. 
Pagination - the table display 10 merchants per page. To access the next batch of 10 merchants, the user can click on "next" button at the end of the table, or the user can click on "previous" to go back to the previous 10 merchants. 

implementation details: 
1. querying RestDB - data is retrieved using RestDB's query language. I set up a dictionary of fields I want to check in the database. Then, I used the JSON stringify method to translate the dictionary to RestDB's language. 
2. display table -  I initiated three arrays. myArray stores the originally queries data from the search tab. filteredArray stores the data after filtering its activiity. displayArray stores the 10 merchants that are currently being displayed. 
3. search tab - an event handler takes care of every key release. This include when user backspaces in the tab. The query will reset itself to default whenever a key is pressed i the search tab. 
