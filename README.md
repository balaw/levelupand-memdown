# levelupand-memdown

this with arow funcoins

```js
const levelup = require('levelup');
const leveldown = require('leveldown');

// Define the path for the .dat file
const filePath = 'file.dat';

// Create a LevelUP instance with LevelDOWN as the storage backend
const db = levelup(leveldown(filePath));

// Put some data into the database
db.put('key1', 'value1', (err) => {
  if (err) {
    console.error('Error putting data:', err);
    return;
  }

  // Read the data from the database
  db.get('key1', (err, value) => {
    if (err) {
      console.error('Error getting data:', err);
      return;
    }

    console.log('Value for key1:', value);

    // Close the database
    db.close((err) => {
      if (err) {
        console.error('Error closing the database:', err);
      }
    });
  });
});

// Optionally, you can use events to handle open and close events
db.on('open', () => {
  console.log('Database opened');
});

db.on('close', () => {
  console.log('Database closed');
});

```


this with no arow functions
```js

const levelup = require('levelup');
const leveldown = require('leveldown');

const filePath = 'file.dat';

const db = levelup(leveldown(filePath));

db.put('key1', 'value1', function (err) {
  if (err) {
    console.error('Error putting data:', err);
    return;
  }

  db.get('key1', function (err, value) {
    if (err) {
      console.error('Error getting data:', err);
      return;
    }

    console.log('Value for key1:', value);

    db.close(function (err) {
      if (err) {
        console.error('Error closing the database:', err);
      }
    });
  });
});

db.on('open', function () {
  console.log('Database opened');
});

db.on('close', function () {
  console.log('Database closed');
});
```
