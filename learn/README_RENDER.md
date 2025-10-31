# Deploying to Render

This guide explains how to deploy this Spring Boot application to Render.

## Quick Deploy Steps

1. **Push your code to GitHub/GitLab/Bitbucket**
   - Make sure all files are committed and pushed to your repository

2. **Deploy on Render:**
   - Go to [Render Dashboard](https://dashboard.render.com/)
   - Click "New +" → "Web Service"
   - Connect your Git repository
   - Render will auto-detect Java/Maven from `render.yaml`
   - Or manually configure:
     - **Build Command**: `./mvnw clean package -DskipTests`
     - **Start Command**: `java -jar target/learn-0.0.1-SNAPSHOT.jar`
     - **Environment**: Java 17

3. **Configuration:**
   - The application automatically uses the `PORT` environment variable provided by Render
   - If deploying manually, Render will auto-detect the settings from `render.yaml`

## Important Notes

- **Port Configuration**: The app uses `${PORT:8080}` - Render provides PORT automatically
- **Health Check**: Endpoint `/iclock/getrequest?SN=HEALTH_CHECK` can be used for health checks
- **Java Version**: Requires Java 17
- **Build**: Uses Maven Wrapper (`mvnw`) for consistent builds

## Testing Endpoints

Once deployed, test your endpoints:
- `GET https://your-app.onrender.com/iclock/getrequest?SN=TEST123`
- `POST https://your-app.onrender.com/iclock/cdata?SN=TEST123&table=ATTLOG`

## Environment Variables (Optional)

If you need to set any environment variables:
- Go to Render Dashboard → Your Service → Environment
- Add any required variables

