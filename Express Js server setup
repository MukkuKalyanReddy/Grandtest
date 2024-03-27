// server.js

const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');

const app = express();
const PORT = process.env.PORT || 5000;

app.use(cors());
app.use(express.json());

// Connect to MongoDB Atlas
mongoose.connect('mongodb+srv://<username>:<password>@<cluster-url>/<database>?retryWrites=true&w=majority', {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

// Create Mongoose Schema and Model for the data
const dataSchema = new mongoose.Schema({
  name: String,
  position: String,
  offe: String,
  startDate: Date,
  att: String,
  we: String,
  sanPremi: Number,
});

const DataModel = mongoose.model('Data', dataSchema);

// Define API endpoint to fetch data
app.get('/api/data', async (req, res) => {
  try {
    const data = await DataModel.find();
    res.json(data);
  } catch (error) {
    res.status(500).json({ message: error.message });
  }
});

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
