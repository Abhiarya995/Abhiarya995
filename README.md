- 👋 Hi, I’m @Abhiarya995
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
// First install the nylas-sdk package: npm i nylas
const Nylas = require("nylas");
const Draft = require("nylas/lib/models/draft.js");
const apiServer = "https://api.nylas.com";
const clientId = "a94u9klvmi8rb4h3o0ldc2h52";
const clientSecret = "bhjtugkk3cu9o9gbbdu1ta661";
const accessToken = "9MmYhHF9Sa3eiVuJF2ZXqkdMmLzpqQ";

Nylas.config({ apiServer, clientId, clientSecret });

const nylas = Nylas.with(accessToken);

// Create a draft email
const draft = new Draft.default(nylas, {
  subject: "With Love, from Nylas",
  body: "This email was sent using the Nylas email API. Visit https://nylas.com for details.",
  to: [{ name: "Nylas", email: "haddikarya@gmail.com" }],
});

// Send the email
draft.send()
     .then((message) => {
       console.log(`Message "${message.subject}" was sent with ID ${message.id}`);
     })
     .catch((err) => {
       console.error("Error:\n", err);
     })
