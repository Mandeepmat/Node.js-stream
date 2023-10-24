# Node.js-stream
How to Write huge amounts of data using stream in Node.js
const fs = require('fs');

// Define the file path where you want to write the data
const filePath = 'huge_data.txt';

// Create a writable stream
const writableStream = fs.createWriteStream(filePath);

// Generate a large amount of data (for demonstration purposes)
const data = 'This is a line of data.\n'.repeat(1000000); // Creating 1 million lines of data

// Write the data to the stream
writableStream.write(data, 'utf-8', () => {
  console.log('Data has been written to the file.');
  // Once all data is written, close the stream
  writableStream.end();
});

// Handle stream events
writableStream.on('finish', () => {
  console.log('Write operation is complete.');
});

writableStream.on('error', (err) => {
  console.error('Error writing data:', err);
});
