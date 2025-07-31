# Deployment Guide

This guide will help you deploy the ConnectPro Social Media App to various platforms.

## 🚀 Deployment Options

### 1. Heroku Deployment

#### Prerequisites
- Heroku account
- Heroku CLI installed
- Git repository

#### Steps

1. **Install Heroku CLI**
   ```bash
   # macOS
   brew tap heroku/brew && brew install heroku
   
   # Windows
   # Download from https://devcenter.heroku.com/articles/heroku-cli
   ```

2. **Login to Heroku**
   ```bash
   heroku login
   ```

3. **Create Heroku App**
   ```bash
   heroku create your-app-name
   ```

4. **Set Environment Variables**
   ```bash
   heroku config:set MONGO_URL=your_mongodb_atlas_url
   heroku config:set JWT_SECRET=your_jwt_secret
   heroku config:set NODE_ENV=production
   ```

5. **Deploy Backend**
   ```bash
   cd server
   git add .
   git commit -m "Deploy backend"
   git push heroku main
   ```

6. **Deploy Frontend**
   ```bash
   cd client
   npm run build
   # Upload build folder to a static hosting service like Netlify or Vercel
   ```

### 2. Vercel Deployment (Frontend)

1. **Install Vercel CLI**
   ```bash
   npm i -g vercel
   ```

2. **Deploy Frontend**
   ```bash
   cd client
   vercel
   ```

3. **Configure Environment Variables**
   - Go to Vercel dashboard
   - Add `REACT_APP_API_URL` pointing to your backend

### 3. Netlify Deployment (Frontend)

1. **Build the Project**
   ```bash
   cd client
   npm run build
   ```

2. **Deploy to Netlify**
   - Drag and drop the `build` folder to Netlify
   - Or connect your GitHub repository

3. **Set Environment Variables**
   - Go to Site settings > Environment variables
   - Add `REACT_APP_API_URL`

### 4. Railway Deployment (Backend)

1. **Connect GitHub Repository**
   - Go to Railway dashboard
   - Connect your GitHub repository

2. **Set Environment Variables**
   ```bash
   MONGO_URL=your_mongodb_atlas_url
   JWT_SECRET=your_jwt_secret
   PORT=3001
   ```

3. **Deploy**
   - Railway will automatically deploy from your main branch

## 🌐 Domain Configuration

### Custom Domain Setup

1. **Purchase Domain**
   - Buy a domain from providers like Namecheap, GoDaddy, etc.

2. **Configure DNS**
   - Point your domain to your hosting provider
   - Add CNAME records for subdomains

3. **SSL Certificate**
   - Most hosting providers offer free SSL certificates
   - Enable HTTPS for security

## 🔧 Environment Variables

### Required Variables

```env
# Database
MONGO_URL=mongodb+srv://username:password@cluster.mongodb.net/database

# Authentication
JWT_SECRET=your_super_secret_jwt_key

# Server
PORT=3001
NODE_ENV=production

# Frontend (if needed)
REACT_APP_API_URL=https://your-backend-url.com
```

### Optional Variables

```env
# CORS
CORS_ORIGIN=https://your-frontend-url.com

# File Upload
MAX_FILE_SIZE=5242880
```

## 📊 Database Setup

### MongoDB Atlas

1. **Create Cluster**
   - Sign up for MongoDB Atlas
   - Create a new cluster

2. **Configure Network Access**
   - Add your IP address or `0.0.0.0/0` for all IPs

3. **Create Database User**
   - Create a user with read/write permissions

4. **Get Connection String**
   - Copy the connection string
   - Replace `<password>` with your user password

### Local MongoDB

1. **Install MongoDB**
   ```bash
   # macOS
   brew install mongodb-community
   
   # Ubuntu
   sudo apt-get install mongodb
   ```

2. **Start MongoDB**
   ```bash
   sudo systemctl start mongod
   sudo systemctl enable mongod
   ```

## 🔒 Security Considerations

### Production Security

1. **Environment Variables**
   - Never commit `.env` files
   - Use secure environment variable management

2. **CORS Configuration**
   ```javascript
   app.use(cors({
     origin: process.env.CORS_ORIGIN || "http://localhost:3000",
     credentials: true
   }));
   ```

3. **Rate Limiting**
   ```javascript
   const rateLimit = require('express-rate-limit');
   
   const limiter = rateLimit({
     windowMs: 15 * 60 * 1000, // 15 minutes
     max: 100 // limit each IP to 100 requests per windowMs
   });
   
   app.use(limiter);
   ```

4. **Input Validation**
   - Validate all user inputs
   - Sanitize data before storing

## 📈 Performance Optimization

### Backend Optimization

1. **Database Indexing**
   ```javascript
   // Add indexes to frequently queried fields
   db.posts.createIndex({ "createdAt": -1 });
   db.users.createIndex({ "email": 1 });
   ```

2. **Caching**
   ```javascript
   const redis = require('redis');
   const client = redis.createClient();
   
   // Cache frequently accessed data
   app.get('/posts', async (req, res) => {
     const cached = await client.get('posts');
     if (cached) {
       return res.json(JSON.parse(cached));
     }
     // ... fetch from database
   });
   ```

### Frontend Optimization

1. **Code Splitting**
   ```javascript
   const HomePage = lazy(() => import('./scenes/homePage'));
   ```

2. **Image Optimization**
   - Use WebP format
   - Implement lazy loading
   - Compress images

## 🐛 Troubleshooting

### Common Issues

1. **CORS Errors**
   - Check CORS configuration
   - Verify frontend URL in backend CORS settings

2. **Database Connection Issues**
   - Verify MongoDB connection string
   - Check network access settings

3. **Build Failures**
   - Check Node.js version compatibility
   - Verify all dependencies are installed

4. **Environment Variables**
   - Ensure all required variables are set
   - Check variable names and values

### Debug Mode

```javascript
// Enable debug logging
const debug = require('debug')('app:server');
app.use((req, res, next) => {
  debug(`${req.method} ${req.url}`);
  next();
});
```

## 📞 Support

For deployment issues:
- Check the platform's documentation
- Review error logs
- Contact platform support
- Open an issue in the repository

---

**Happy Deploying! 🚀** 