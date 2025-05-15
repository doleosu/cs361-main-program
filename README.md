Microservice A - Communication Contract

A. How to progammatically REQUEST Data:

To request sorted data from the microservice send a POST request to http://localhost:5001/sort-events with appropriate header and JSON body structure, shown in the example below.

Example of requesting data:

fetch('http://localhost:5001/sort-events', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        events: [
            {
                date: '2025-05-20T00:00:00.000Z',
                artist: 'The Weeknd',
                description: 'Kissland',
                location: 'Chicago, IL'
            },
            {
                date: '2025-06-10T00:00:00.000Z',
                artist: 'Adele',
                description: '25 Tour',
                location: 'New York, NY'
            }
        ],
        order: 'asc'
    })
});

The microservice will then, sort the data and then send it back to your server, in order to receive the data, see the example below.

B. How to programmatically RECEIVE data

Use the following example to receivethe sorted data from the microservice:

fetch('http://localhost:5001/sort-events', { /* request options as above */ })
    .then(response => response.json())  // parse JSON response
    .then(sortedEvents => {
        
        // update the display
        renderEvents(sortedEvents);
    });

C. UML Sequence Diagram