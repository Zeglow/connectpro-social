# ConnectPro Social Platform

A full-stack social media application built with the MERN stack (MongoDB, Express.js, React, Node.js) featuring modern UI/UX design, real-time interactions, and comprehensive social networking features.

![ConnectPro Social Media App](https://img.shields.io/badge/React-18.2.0-blue?style=for-the-badge&logo=react)
![Node.js](https://img.shields.io/badge/Node.js-20.15.0-green?style=for-the-badge&logo=node.js)
![MongoDB](https://img.shields.io/badge/MongoDB-6.7.0-green?style=for-the-badge&logo=mongodb)
![Express.js](https://img.shields.io/badge/Express.js-4.18.2-black?style=for-the-badge&logo=express)

## 🌟 Features

### Core Social Media Features
- **User Authentication** - Secure JWT-based login/registration system
- **Post Creation** - Create and share posts with text and images
- **Real-time Interactions** - Like posts and view engagement metrics
- **User Profiles** - Personalized user profiles with customizable information
- **Friend System** - Add and manage friends
- **Responsive Design** - Optimized for desktop, tablet, and mobile devices

### Advanced Features
- **Dark/Light Mode** - Toggle between themes for better user experience
- **Image Upload** - Drag-and-drop image upload functionality
- **Real-time Updates** - Posts appear at the top immediately after creation
- **Profile Statistics** - Track profile views and post impressions
- **Comment System** - Engage with posts through comments
- **Modern UI/UX** - Material-UI components with beautiful design

## 🛠️ Technology Stack

### Frontend
- **React 18** - Modern React with hooks and functional components
- **Redux Toolkit** - State management with RTK Query
- **Material-UI (MUI)** - Beautiful and responsive UI components
- **React Router** - Client-side routing
- **Formik & Yup** - Form handling and validation
- **React Dropzone** - File upload functionality

### Backend
- **Node.js** - Server-side JavaScript runtime
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database with Mongoose ODM
- **JWT** - JSON Web Tokens for authentication
- **bcrypt** - Password hashing and security
- **Multer** - File upload middleware
- **CORS** - Cross-origin resource sharing
- **Helmet** - Security middleware

### Development Tools
- **Nodemon** - Auto-restart server during development
- **ES6 Modules** - Modern JavaScript module system

## 📦 Installation

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or cloud instance)
- npm or yarn package manager

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/connectpro-social.git
   cd connectpro-social
   ```

2. **Install server dependencies**
   ```bash
   cd server
   npm install
   ```

3. **Install client dependencies**
   ```bash
   cd ../client
   npm install
   ```

4. **Environment Configuration**

   Create a `.env` file in the `server` directory:
   ```env
   MONGO_URL=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_key
   PORT=3001
   ```

5. **Database Setup**
   - Set up a MongoDB database (local or MongoDB Atlas)
   - Update the `MONGO_URL` in your `.env` file
   - The application will automatically create collections and load sample data

## 🚀 Running the Application

### Development Mode

1. **Start the backend server**
   ```bash
   cd server
   npm start
   ```
   Server will run on `http://localhost:3001`

2. **Start the frontend application**
   ```bash
   cd client
   npm start
   ```
   Application will run on `http://localhost:3000`

### Production Build

1. **Build the frontend**
   ```bash
   cd client
   npm run build
   ```

2. **Deploy the backend**
   ```bash
   cd server
   npm start
   ```

## 📱 Usage

### Getting Started
1. Open the application in your browser at `http://localhost:3000`
2. Register a new account or login with existing credentials
3. Start creating posts, adding friends, and engaging with the community

### Test Account
- **Email**: `test@test.com`
- **Password**: `test123`

### Key Features
- **Create Posts**: Click the "What's on your mind..." input to create new posts
- **Upload Images**: Use the image upload feature to add visuals to your posts
- **Like Posts**: Click the heart icon to like posts
- **View Profiles**: Click on user names to view their profiles
- **Toggle Theme**: Switch between dark and light modes using the theme toggle

## 🏗️ Project Structure

```
connectpro-social/
├── client/                 # React frontend
│   ├── public/            # Static files
│   ├── src/
│   │   ├── components/    # Reusable components
│   │   ├── scenes/        # Page components
│   │   ├── state/         # Redux store
│   │   └── theme.js       # Material-UI theme
│   └── package.json
├── server/                # Node.js backend
│   ├── controllers/       # Route controllers
│   ├── middleware/        # Custom middleware
│   ├── models/           # Mongoose models
│   ├── routes/           # API routes
│   ├── data/             # Sample data
│   └── package.json
└── README.md
```

## 🔧 API Endpoints

### Authentication
- `POST /auth/register` - User registration
- `POST /auth/login` - User login

### Posts
- `GET /posts` - Get all posts (sorted by creation time)
- `POST /posts` - Create new post
- `PATCH /posts/:id/like` - Like/unlike a post
- `GET /posts/:userId/posts` - Get user's posts

### Users
- `GET /users/:id` - Get user profile
- `PATCH /users/:id/:friendId` - Add/remove friend

## 🎨 Customization

### Theme Customization
Edit `client/src/theme.js` to customize colors, typography, and other theme properties.

### Adding New Features
- **New API endpoints**: Add routes in `server/routes/`
- **New components**: Create components in `client/src/components/`
- **New pages**: Add scenes in `client/src/scenes/`


## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

This project is based on the excellent work by **[Ed Roh](https://github.com/ed-roh)** and his [MERN Social Media App](https://github.com/ed-roh/mern-social). 

**Original Project**: [https://github.com/ed-roh/mern-social](https://github.com/ed-roh/mern-social-media)

**YouTube Tutorial**: [Build a COMPLETE Fullstack Responsive MERN App](https://www.youtube.com/watch?v=K8YELRmUb5o)

### Enhancements Made
- ✅ Fixed post sorting to display newest posts at the top
- ✅ Improved image upload functionality
- ✅ Enhanced user experience with automatic page refresh


