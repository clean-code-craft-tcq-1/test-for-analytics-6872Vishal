# Test for Analytics

Design tests for Analytics functionality on a Battery Monitoring System.

Fill the parts marked '_enter' in the **Tasks** section below.

## Analysis-functionality to be tested

This section lists the Analysis for which _tests_ must be written.

Battery Telemetrics are collected and stored on a server.
Data for a month is stored in a [csv file](https://en.wikipedia.org/wiki/Comma-separated_values).

Analysis must be done on this csv file to find the following:
- minimum
- maximum
- count of breaches (how many times did it cross the threshold in a month?)
- record trends (date & time when the reading was continuously increasing for 30 minutes)

A PDF report of the analysis must be stored every week.
Notification must be sent when a new report is available.

## Tasks

### List Dependencies

List the dependencies of the Analysis-functionality.

1. Access to the Server containing the telemetrics in a csv file
2. Storage space in the server for csv file and PDF file.
3. Thershold values 
4. PDF file format
5. Vaild csv file data
6. server should be online.

(add more if needed)

### Mark the System Boundary

What is included in the software unit-test? What is not? Fill this table.

| Item                      | Included?     | Reasoning / Assumption
|---------------------------|---------------|---
Battery Data-accuracy       | No            | We do not test the accuracy of data
Computation of maximum      | Yes           | This is part of the software being developed
Off-the-shelf PDF converter | No            | Security risk 
Counting the breaches       | Yes           | System requirement is to check no of breaches.
Detecting trends            | Yes           | Requirement to check if the breach exceeds more than 30 min or not
Notification utility        | Yes           | Notifing the user is part of the Analysis 

### List the Test Cases

Write tests in the form of `<expected output or action>` from `<input>` / when `<event>`

Add to these tests:

1. Write minimum and maximum to the PDF from a csv containing positive and negative readings
2. Write "Invalid input" to the PDF when the csv doesn't contain expected data
3. Write Min and Max to the PDF file when csv analysis is completed
4. Write the no of breaches to PDF file when csv file analysis is completed 
5. Write the Timestamp if the breach exceeds the time limit of 30min
6. Write Access denied to the PDF if the system can't enter the server 
7. write Invalid csv file to the PDF if the input to the server is corrupted
8. Notify the user after compeletion of the report
9. Store PDF in server after compeletion of the analysis
10. Write file not avaliable in PDF if csv file is not updated for the month

(add more)

### Recognize Fakes and Reality

Consider the tests for each functionality below.
In those tests, identify inputs and outputs.
Enter one part that's real and another part that's faked/mocked.

| Functionality            | Input        | Output                      | Faked/mocked part
|--------------------------|--------------|-----------------------------|---
Read input from server     | csv file     | internal data-structure     | Fake the server store
Validate input             | csv data     | valid / invalid             | None - it's a pure function
Notify report availability | Report\PDF   | done \ Not done             | Fake the Notification with report
Report inaccessible server |server details|    Access denied\allowed    | Mock the server entry 
Find minimum and maximum   | csv data     | Max and Min info            | Fake the csv file data input to check Max and Min
Detect trend               | csv data     | Pass\fail                   | Fake the csv file data to detect the trend
Write to PDF               |Analysed info |   PDF file                  | Fake the inputs to check the PDF 
 
