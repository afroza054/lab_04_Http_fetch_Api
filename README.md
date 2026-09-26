# lab_04_Http_fetch_Api
Http, Fetch and simple API use
1.	Objective 
The main objectives of Lab 04 are:
•	To understand the basic HTTP request-response process.
•	To understand how a web page can request data from a JSON file using the Fetch API.
•	To use JavaScript fetch() to make GET requests.
•	To process JSON responses using response.json().
•	To display dynamically loaded data on a webpage.
•	To understand HTTP status code 200 and handle unsuccessful requests.
•	To practice using a public REST API.
•	To test and debug API requests using browser Developer Tools.

2.	Tools Used
The following tools were used to complete Lab 04:
•	Visual Studio Code – for writing and editing HTML, Json and JavaScript.
•	Web Browser – for running and testing the webpage.
•	Live Server — for running the webpage through a local HTTP server.
•	GitHub – for storing and submitting the project repository.
•	HTML – for creating the webpage structure.
•	JavaScript – for adding interaction and dynamic behavior.

3.	Request-Response Understanding 
GET Request: A GET request is an HTTP request used by a client, such as a web browser, to request data from a server. In this lab, JavaScript uses the Fetch API to send a GET request for the workshop.json file. For example:
const response = await fetch("data/workshop.json"); The browser requests the JSON file from the server.
Response: After receiving the request, the server sends a response back to the browser. The response contains information such as the HTTP status code and the requested data. Status 200
HTTP status code 200 (OK) means that the request was successfully received and processed. In this lab, a status of 200 indicates that workshop.json was successfully found and returned.
JSON Response: JSON (JavaScript Object Notation) is a lightweight data format commonly used for transferring structured data between systems. The workshop information is stored as JSON:
{"title": "Practical Web Development",  "date": "15 oct 2026", "venue": "seu Lab", "seats": 40, coursefee:5000}
JavaScript converts the JSON response into a JavaScript object so that individual values can be displayed on the webpage.

4.	Implementation Evidence
The implementation consists of three main parts: HTML, JavaScript, and JSON.
HTML: The webpage contains a button that calls the 
loadWorkshop() function:
<button type="button" onclick="loadWorkshop()">
    Load Workshop
</button>
The returned workshop information is displayed using elements with specific IDs:
<p><strong>Title:</strong>
    <span id="workshopTitle">Not Loaded</span>
</p>
<p><strong>Date:</strong>
    <span id="workshopDate">Not Loaded</span>
</p>
<p><strong>Venue:</strong>
    <span id="workshopVenue">Not Loaded</span>
</p>
<p><strong>Seats:</strong>
    <span id="workshopSeats">Not Loaded</span>
</p>

JavaScript
The loadWorkshop() function requests the JSON file and displays its returned values:
async function loadWorkshop() {
    document.getElementById("loadMessage").textContent = "Loading...";

    const response = await fetch("data/workshop.json");

    if (response.status === 200) {
        const workshop = await response.json();

        document.getElementById("workshopTitle").textContent = workshop.title;
        document.getElementById("workshopDate").textContent = workshop.date;
        document.getElementById("workshopVenue").textContent = workshop.venue;
        document.getElementById("workshopSeats").textContent = workshop.seats;

        document.getElementById("loadMessage").textContent =
            "Workshop data loaded successfully.";
    }
}

5.	Network Evidence:
Browser Developer Tools were used to verify that the JSON file was successfully requested.
After clicking the Load Workshop button, the browser sends a GET request for:
	data/workshop.json
In the Network panel, the request should show:
Request: workshop.json
Method: GET
Status: 200
The response contains the workshop JSON data.
Screenshot to include:
 
This confirms that the browser successfully requested and received the JSON file from the server.

6.	Keycode explanation
fetch()
The fetch() function is used to make an HTTP request.
const response = await fetch("data/workshop.json");
Here, the browser sends a GET request to retrieve workshop.json.
await
await pauses the execution of the asynchronous function until the requested operation is completed.
const response = await fetch("data/workshop.json");
This allows the program to wait for the server response before processing it.
response.status
response.status provides the HTTP status code returned by the server.
if (response.status === 200) {
A status of 200 indicates that the request was successful.
response.json()
The response.json() method reads the JSON response and converts it into a JavaScript object.
const workshop = await response.json();
After conversion, individual properties can be accessed:
workshop.title
workshop.date
workshop.venue
workshop.seats
workshop.coursefee

7. Testing and Debugging
Successful Test
The first test was performed by running the webpage using Live Server and clicking the Load Workshop button.
The browser successfully requested:
data/workshop.json
The server returned status 200, and the JSON data was displayed on the webpage:
•	Title: Practical Web Development
•	Date: 15 oct 2026
•	Venue: seu Lab
•	Seats: 40
• Course Fee: 5000
The Network panel was also checked to confirm that workshop.json returned status 200.
Controlled 404 Test
A controlled 404 test was performed by intentionally changing the JSON file path to an incorrect path, for example:
fetch("data/workshop-not-found.json");
Since the requested file does not exist, the server returns:
404 Not Found
This test demonstrates the difference between a successful request and a missing resource.
The path was then corrected back to:
fetch("data/workshop.json");
After correcting the path, the request returned status 200 and the workshop information was displayed successfully.
Mistake Corrected
One issue encountered during testing was that the JSON data did not initially load when the HTML file was opened directly. The problem was related to using fetch() with a local file:// URL.
The issue was corrected by running the project through Live Server, which provides the webpage through an HTTP server. After doing this, the browser was able to request data/workshop.json successfully.

8. GitHub Link
GitHub Repository: https://github.com/afroza054/lab_04_Http_fetch_Api
The repository contains the files for Lab 05, including the HTML, JavaScript, JSON, CSS, and related project files.

9. Learning Reflection
The most important idea I learned from this lab is how the Fetch API allows JavaScript to communicate with a server and retrieve data without manually writing a separate HTTP request. I learned how a GET request is sent, how the server responds with a status code and data, and how JSON can be converted into a JavaScript object.
One challenge I faced was getting the local JSON file to load correctly. Initially, the workshop data was not displayed because the webpage was being opened directly rather than through a local HTTP server. I investigated the problem and learned that using Live Server allows the browser to make the required HTTP request.
