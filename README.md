# AWS EC2 Application with Load Balancer Support

This is a basic Node.js application designed to work with AWS EC2 and Application Load Balancer (ALB).

## Features
- Health check endpoint at `/`
- Ready for ALB target group integration
- Simple status response with timestamp

## Local Setup
1. Install dependencies:
   ```bash
   npm install
   ```
2. Start the application:
   ```bash
   npm start
   ```

## AWS Deployment Steps

### EC2 Setup
1. Launch an EC2 instance with Amazon Linux 2
2. Install Node.js:
   ```bash
   curl -fsSL https://rpm.nodesource.com/setup_18.x | sudo bash -
   sudo yum install -y nodejs
   ```
3. Clone your application to the EC2 instance
4. Install dependencies and start the application

### Load Balancer Setup
1. Create a Target Group:
   - Target type: Instances
   - Protocol: HTTP
   - Port: 3000
   - Health check path: `/`
   - Success codes: 200

2. Create an Application Load Balancer:
   - Scheme: Internet-facing
   - Listeners: HTTP on port 80
   - Configure routing to the target group

3. Add your EC2 instance to the target group

## Health Check Response
The application responds to the root path (`/`) with a JSON payload:
```json
{
    "status": "healthy",
    "message": "Application is running",
    "timestamp": "[current-timestamp]"
}
```