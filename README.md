MilBaithak – Language Exchange Platform (MERN + Stream Video SDK)

MilBaithak is a full-stack MERN platform designed for language learners to connect with matching partners, chat in real-time, make video calls, exchange friend requests, and customize themes.
The system intelligently suggests users based on native and learning languages, giving the best matching experience.

This project includes:
User Authentication (Signup, Login, Logout)
User Onboarding (Native + Learning Language Selection)
Real-time Chat
Video Calling (using Stream Video SDK)
Friend Requests & Notifications
Friend Suggestions
Theme Switching (Zustand + DaisyUI)
Protected Routes


⭐ Live Demo
✨ https://milbaithak.onrender.com/

 
🎥 Project Demo Video:
https://drive.google.com/file/d/1lMyxp04VJqIqbKR1VIWRxW-aNxVO9Mfi/view?usp=sharing


🚀 Features
✅ Authentication
Signup with profile picture
Secure login
Logout
JWT + Cookies based auth
Protected API routes

✅ Onboarding
User selects:
Native Language
Learning Language
Stored in DB

Used for recommendation algorithm

✅ User Suggestions
Smart matching based on:
nativeLanguage of User A == learningLanguage of User B
AND
learningLanguage of User A == nativeLanguage of User B


This ensures both users can learn from each other.

✅ Friend Requests
Send friend request
Accept friend request
See incoming & outgoing requests
Notifications page

✅ Chat System
Real-time messaging
Chat UI
Auto-scroll
Smooth experience

✅ Video Calling
Integrated with Stream Video SDK
Secure token from backend
Call room with:
Mute/Unmute
Camera On/Off
Leave call
Speaker layout

✅ Theme System
Zustand state
DaisyUI themes
Saved in localStorage
Automatically persists

📂 Project Structure
milbaithak/
 ├── backend/
 │   ├── controllers/
 │   ├── models/
 │   ├── middleware/
 │   ├── routes/
 │   ├── utils/
 │   └── server.js
 │
 └── frontend/
     ├── src/
     │   ├── pages/
     │   ├── components/
     │   ├── store/
     │   ├── hooks/
     │   ├── lib/
     │   └── App.jsx

🔧 Tech Stack
Frontend
React.js
React Router
Zustand
DaisyUI + Tailwind
TanStack React Query
Stream Video SDK
Lucide Icons
Backend
Node.js
Express.js
MongoDB + Mongoose
JWT
Stream Server Token
Cookie Auth

🛠 Installation & Setup
Clone Repository
git clone https://github.com/NavinMalakar2/MilBaithak.git
cd milbaithak

📌 Backend Setup
Install Dependencies
cd backend
npm install

Create .env
PORT=8000
MONGO_URI=your_mongodb_uri
JWT_SECRET=your_jwt_secret
STREAM_API_KEY=your_stream_api_key
STREAM_SECRET=your_stream_secret
CLIENT_URL=http://localhost:5173

Start Server
npm run dev


Backend will run on:

http://localhost:8000

📌 Frontend Setup
Install Dependencies
cd frontend
npm install

Add .env File
VITE_STREAM_API_KEY=your_stream_api_key
VITE_BACKEND_URL=http://localhost:8000/api

Start Frontend
npm run dev


Frontend will run on:

http://localhost:5173

🔒 Protected Routes Logic
JWT + Cookies
When login/signup → token stored in HTTP-only cookie
Every protected route checks user through protectRoute middleware

Example:
router.get("/me", protectRoute, (req, res) => {
  res.status(200).json({ user: req.user });
});

🤝 Friend Suggestion Logic

Backend code:
const users = await User.find({
  _id: { $ne: req.user._id },
  nativeLanguage: req.user.learningLanguage,
  learningLanguage: req.user.nativeLanguage,
});


👉 This gives perfect language-exchange match.

🎥 Video Calling Flow

Frontend requests token:
/chat/token

Backend returns token generated using Stream Server SDK

React client initializes:

new StreamVideoClient({
  apiKey: STREAM_API_KEY,
  user,
  token,
});


Join call:

call.join({ create: true });


👨‍💻 1 Author
Navin Malakar
✨ MERN Stack Developer
🔗 Portfolio link https://3d-portfolio-navin.vercel.app/

