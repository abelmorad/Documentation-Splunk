# Documentation: Querying with Splunk #01

## 1. Introduction
Purpose: Document my experience and share knowledge on the Google cybersecurity certificate program
Scope: Learn the foundations of cybersecurity and prepare for a career as a cybersecurity analyst

## 2. Setup
- Environment: Windows OS, Brave browser, and Splunk Cloud
- Accounts and Access: Google, coursera, and splunk accounts

## 3. Challenge Walkthrough

### 3.1 Lesson: SIEM Tools
- **Objective**: Perform a query with Splunk to locate failed SSH login(s) for the root account

### 3.2: Procedure

- Download tutorialdata.zip file
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/587bce49-5992-480e-bbe9-36db82a7eb79)

- Click Add data
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/29c9ce07-072b-4aac-bdd7-dbd3335b6d0a)

- Click upload
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/14c07ba5-6e1f-440f-b9a7-51dffe55325a)

- Select a file and select tutorialdata.zip then click next
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/b88157ba-6b30-46c9-ba99-5f3c78c1b84a)

- By the host section select Segment in the path and enter 1 as the segment number
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/eb513d8a-1f9d-4afd-9413-dade17314a3a)

- Click the review button
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/b94ea46f-d517-41c6-a613-7ff9ca2185b7)
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/17bd5ba7-0a6a-4a46-9c4c-29e6114a056a)

- Click submit button

- On the homepage click search & reporting
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/a1c52c7b-9cd8-48a0-a30c-c8c18eb7c2dd)

- In the search bar type `index=main` this search term specifies the index. An index is a repository for data. Here, the index is a single dataset containing events from an index named main.
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/146083bd-8c41-4107-b5c1-597047ca93fc)

- Click the range dropdown menu and select All time
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/4f0ce97b-9edc-4ec2-8a1f-81ce6984fffa)
 
- Click the search button or press enter. Note that the search button is represented by the magnifying glass icon. Your search should retrieve thousands of events.

- Evaluate the fields. For each event the fields are host, source, and sourcetype. Under SELECTED FIELDS, examine the same fields.
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/56b59171-fbd9-42ac-b236-b6939df083d8)
  - Examine the field values by clicking on the field under SELECTED FIELDS. You should observe the following:
    - ***host***: The host field specifies the name of the network host from which the event originated. In this search there are five hosts:
      ![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/e1501ab7-3c96-4ee7-a2ed-fdd98078ccf6)
    - ***source***: The source field indicates the file name from which the event originates. You should identify eight sources. Notice /mailsv/secure.log which is a log file that contains information related to authentication and authorization attempts on the mail server.
      
      ![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/ffb98306-99f0-4c0a-b766-283c25ac7943)
    - ***sourcetype***: The sourcetype determines how data is formatted. You should observe three sourcetypes. Examine secure-2.
      ![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/09089b8a-a536-4e50-aa9e-7f85e4281ac5)

- Narrow search by clicking host and click mailsv
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/911502f3-7000-4cfa-bade-33add7ae3748)

- Continue to narrow the search to locate any failed SSH logins for the root account. In the search bar enter `index=main host=mailsv fail* root`. This search expands on the search from the previous task and searches for the keyword fail*. The wildcard tells Splunk to expand the search term to find other terms that contain the word fail such as failure, failed, etc. Lastly, the keyword root searches for any event that contains the term root. Press Enter.
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/2aea47db-a711-4c60-b7b6-b6d1265bf26d)

- Result
![image](https://github.com/abelmorad/Documentation-Splunk/assets/110463619/5d0f0a72-c9bc-4b1c-a0e6-18b3db1d3883)
 - There are a total of 109,864 events
 - There are 346 failed ssh logins for the root account on the mail server

## 5. Analysis and Reflection
- Learnings: Querying in splunk

## 6. Conclusion
- Summary: Successfully determined the failed ssh logins on the mail server's root account
  
## 7. References
- [https://www.splunk.com/](https://www.splunk.com/)
- [Google Cybersecurity Certificate](https://www.coursera.org/professional-certificates/google-cybersecurity)
- [https://grow.google/certificates/cybersecurity/](https://grow.google/certificates/cybersecurity/)
- [SPL syntax](https://docs.splunk.com/Documentation/Splunk/9.0.2/SearchReference/UnderstandingSPLsyntax)
