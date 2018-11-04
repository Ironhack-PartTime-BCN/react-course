# Express Backend API Setup

- Delete all views files
- Delete all views middleware

## Control errors api

__app.js__ 
```javascript
...
// catch 404 and forward to error handler
app.use((req, res, next) => {
  res.status(404).json({code: 'not found'});
});

app.use((err, req, res, next) => {
  // always log the error
  console.error('ERROR', req.method, req.path, err);

  // only render if the error ocurred before sending the response
  if (!res.headersSent) {
    res.status(500).json({code: 'unexpected'});
  }
});
...
```

## CORS Setup

```bash
$ npm install cors --save
```

```javascript
const cors = require('cors');

// const app = express();

app.use(cors({
  credentials: true,
  origin: ['http://localhost:3000']
}));

```