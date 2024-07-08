const express = require('express');
const bodyParser = require('body-parser');

const app = express();
const port = process.env.PORT || 3000;

app.use(bodyParser.json());

app.post('/convert', (req, res) => {
    const { url } = req.body;

    if (!url.startsWith('https://www.hagobuy.com/')) {
        return res.status(400).json({ error: 'Invalid HagoBuy URL' });
    }

    const convertedUrl = url.replace('https://www.hagobuy.com/', 'https://hoobuy.com/');

    res.json({ convertedUrl });
});

app.listen(port, () => {
    console.log(`App listening at http://localhost:${port}`);
});
