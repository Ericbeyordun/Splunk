# Splunk
Activity: Perform a query with Splunk
Practice Quiz. • 30 min


English
DueMar 10, 11:59 PM EDT
Congratulations! You passed!
Grade received 100%
To pass 75% or higher

Go to next item
To complete this optional activity, you must follow the step-by-step instructions and receive at least 75%, or 3 out of 4 points, on the questions that follow. Once you have answered the questions, review the feedback statements. You can learn more about the graded and practice items in the 
course overview
.


Activity Overview

In this activity, you'll be introduced to the Splunk platform. Then, you'll use Splunk Cloud to upload data, perform basic searches on the data, and answer a series of questions. Follow the instructions in the 
Follow-along guide for Splunk sign-up
 to complete the following before you begin using Splunk:

Create a Splunk account

Activate a free trial of Splunk Cloud

Upload data into Splunk Cloud

Please note that this activity is optional and will not affect your completion of the course.

So far, you've learned that SIEM tools, such as Splunk, are an important part of a security analyst's toolbox because they provide a platform for storing, analyzing, and reporting on data from different sources. You also explored some basic searches using Splunk's querying language, called Search Processing Language (SPL), which included the use of pipes and wildcards.

Creating effective searches is an important skill because it enables you to quickly and accurately find the information you are looking for within a large amount of data. Quick and accurate searching is especially useful during incident response, because you might need to swiftly identify and address a security incident. Effective search techniques also help you efficiently identify patterns, trends, and anomalies within data.

Scenario

Review the following scenario. Then complete the step-by-step instructions.

You are a security analyst working at the e-commerce store Buttercup Games. You've been tasked with identifying whether there are any possible security issues with the mail server. To do so, you must explore any failed SSH logins for the root account.  

Note: Use the incident handler's journal you started in 
a previous activity
 to take notes during the activity and keep track of your findings.

Step-By-Step Instructions

Follow the instructions and answer the following questions to complete the activity.



Step 1: Access supporting materials
The following supporting materials will help you complete this activity. The data contains log and event information from Buttercup Games' mail servers and web accounts. This includes information like access and authentication logs, email logs, and more.


To download this data, click the link then click the download icon.

Link to supporting materials: 
tutorialdata.zip
 file

OR

If you don’t have a Google account, you can download the supporting materials directly from the following attachment.

tutorialdata
ZIP File


Step 2: Create a Splunk Cloud account
To use Splunk Cloud, you must create an account. Follow Part 1 - Create a Splunk Cloud account and Part 2 - Verify your email in the 
Follow-along guide for Splunk sign-up
 to create an account.


Step 3: Sign up for a free Splunk Cloud trial
After you've created your Splunk account, you'll need to sign up for a free Splunk Cloud trial. Follow Part 3 - Activate a Splunk Cloud trial in the 
Follow-along guide for Splunk sign-up
.

Note: If you experience any issues activating your Splunk Cloud trial please check out the 
Splunk cloud tutorial video
.


Step 4: Upload data into Splunk
To operate effectively, it's essential that SIEM tools ingest and index data. SIEM tools collect and process data so that it becomes searchable events that can be queried, viewed, and analyzed.

So far, you've created a Splunk account and activated and accessed the Splunk Cloud free trial, but your Splunk Cloud instance does not contain any data. Next, you'll need to upload data into Splunk to start querying. Complete the following steps to upload data into Splunk:

If you haven't already, download the data file from Step 1:  
tutorialdata.zip
. Click the link then click the download icon. Do not uncompress the file.

Navigate to Splunk Home from your Splunk Cloud free trial instance. You might need to log in again using your credentials from Step 3.

On the Splunk bar, click Settings. Then click the Add Data icon.

Click Upload.

Click the Select File button.

Upload the tutorialdata.zip file, and click Open.

Click the Next button to continue to Input Settings.

By the Host section, select Segment in path and enter 1 as the segment number.

Click the Review button and review the details of the upload before you submit. The details should be as follows: 

Input Type: Uploaded File
File Name: tutorialdata.zip
Source Type: Automatic
Host: Source path segment number: 1 
Index: Default

Click Submit. Once Splunk has ingested the data, you will receive confirmation that the file was successfully uploaded.

Note: If you are experiencing issues uploading data into Splunk, refer to the 
Splunk Search Tutorial
 guide for help.


Step 5: Perform a basic search
Take a moment to examine the Splunk Cloud interface by locating the app panel, the Explore Splunk panel, and the Splunk bar.


Now that you've uploaded the data into Splunk, perform your first query to confirm that the data has been ingested, indexed, and is searchable. Follow these steps to perform a query:

Navigate to Splunk Home. (To return to Splunk Home, click the Splunk Cloud logo on the Splunk Cloud page.)

Click Search & Reporting. You may close any pop ups that appear.

In the search bar,  enter your search query:
index="main"
This search term specifies the index. An index is a repository for data. Here, the index is a single dataset containing events from an index named main.

Select All Time from the time range dropdown to search for all the events across all time.

Click the search button. Note that the search button is represented by the magnifying glass icon. Your search should retrieve thousands of events.


Pro tip: It's a best practice to use short time ranges in your searches because a shorter time range returns results faster and uses fewer resources. Adjust the time using the time range dropdown or by using 
time modifiers
 in your search.


Step 6: Evaluate the fields
When Splunk indexes data, it attaches fields to each event. These fields become part of the searchable index event data. This helps security analysts easily search for and find the specific data they need. Now that you've run your first query, examine the search results and the fields.

For each event the fields are host, source, and sourcetype. Under SELECTED FIELDS, examine the same fields.


Examine the field values by clicking on the field under SELECTED FIELDS. You should observe the following:

host: The host field specifies the name of the network host from which the event originated. In this search there are five hosts:

mailsv - Buttercup Games' mail server. Examine events generated from this host.

www1 - This is one of Buttercup Games' web applications.

www2 - This is one of Buttercup Games' web applications.

www3 - This is one of Buttercup Games' web applications.

vendor_sales - Information about Buttercup Games' retail sales.

source: The source field indicates the file name from which the event originates. You should identify eight sources. Notice /mailsv/secure.log, which is a log file that contains information related to authentication and authorization attempts on the mail server.

sourcetype: The sourcetype determines how data is formatted. You should observe three sourcetypes. Examine secure-2.


Step 7: Narrow your search
Because you've been tasked with exploring any failed SSH logins for the root account on the mail server, you'll need to narrow the search results for events from the mail server.

Under SELECTED FIELDS, click host and click mailsv.

Notice that a new term has been added to the search bar: index=main host=mailsv. The search results have narrowed to over 9000 events that are generated by the mail server.


Step 8: Search for a failed login for root
Now that you've narrowed your search results to events generated by the mail server, continue to narrow the search to locate any failed SSH logins for the root account. 

Clear the search bar.

Enter index=main host=mailsv fail* root into the search bar.
This search expands on the search from the previous task and searches for the keyword fail*. The wildcard tells Splunk to expand the search term to find other terms that contain the word fail such as failure, failed, etc. Lastly, the keyword root searches for any event that contains the term root.

Click search.


Step 9: Evaluate the search results
Your search from the previous task should have retrieved search results for over 300 events. Navigate to other pages of the search results to observe the events not listed on the first page of results.

Pro tip: Splunk highlights search terms in search results to make it easier to identify where the search terms appear in the data.

Step 10: Answer questions about the search results 

1.
Question 1
How many events are contained in the main index across all time?

Status: [object Object]
1 / 1 point

10-99


10,000


Over 100,000


100-1,000

Correct
Entering a search for all events in the main index retrieves 109,864 events.

2.
Question 2
Which field identifies the name of a network device or system from which an event originates?

Status: [object Object]
1 / 1 point

source


index


sourcetype


host

Correct
The host field specifies the name of a host, such as a network device or other system, from which an event originates.

3.
Question 3
Which of the following hosts used by Buttercup Games contains log information relevant to financial transactions?

Status: [object Object]
1 / 1 point

vendor_sales


www1


www3


www2

Correct
The vendor_sales host provides information about Buttercup Games' retail sales, such as the number of products sold.

4.
Question 4
How many failed SSH logins are there for the root account on the mail server?

Status: [object Object]
1 / 1 point

One


100


More than 100


None

Correct
There are over 100 failed SSH logins for the root account on the mail server.

Key takeaways
In this activity, you used Splunk Cloud to perform a search and investigation. Using Splunk Cloud, you were able to:

Upload sample log data 

Search through indexed data

Evaluate search results

Identify different data sources 

Locate failed SSH login(s) for the root account
