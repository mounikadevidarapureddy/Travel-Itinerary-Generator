# ✈️ Travel Itinerary Generator

A full-stack web application that collects trip details from users, generates personalized travel itineraries using AI (OpenAI), and delivers them via email. Perfect for automating the time-consuming process of creating structured travel plans.

## 🌟 Features

- **Interactive Form**: Beautiful, responsive form collecting all essential trip details
- **AI-Powered Generation**: Uses OpenAI GPT models to create personalized, day-by-day itineraries
- **Email Delivery**: Automatically sends the generated itinerary to the user's email address
- **Validation**: Client-side and server-side validation for all inputs
- **Modern UI**: Clean, dark-themed interface with smooth animations
- **Error Handling**: Comprehensive error messages and user feedback

## 📋 Form Fields

The frontend form collects the following information:

### Required Fields:
- **Starting Location**: Where the trip begins
- **Destination / Location**: Where you're traveling to
- **Number of Days**: Duration of the trip (1-365 days)
- **Budget**: Total budget for the trip
- **Mode of Travel**: Bus, Train, Flight, or Car
- **Number of Travelers**: How many people are traveling
- **Email Address**: Where to send the itinerary

### Optional Fields:
- **Additional Preferences**: Any special requirements (dietary restrictions, accessibility needs, activity preferences, etc.)

## 📁 Project Structure

```
p2_Iphone Calculator/
├── index.html          # Main HTML file with form structure
├── style.css           # Stylesheet with modern dark theme
├── Script.js           # Frontend JavaScript for validation and API calls
├── README.md           # This file
└── server/             # Backend server
    ├── index.js        # Express server with AI & email integration
    ├── package.json    # Node.js dependencies
    └── .env.example    # Environment variables template
```

## 🛠️ Technologies Used

### Frontend:
- **HTML5**: Semantic markup
- **CSS3**: Modern styling with CSS variables, animations, and responsive design
- **Vanilla JavaScript**: No frameworks, pure ES6+ JavaScript

### Backend:
- **Node.js**: Runtime environment
- **Express.js**: Web server framework
- **OpenAI API**: AI-powered itinerary generation
- **Nodemailer**: Email sending functionality
- **CORS**: Cross-origin resource sharing
- **dotenv**: Environment variable management

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (version 18 or higher) - [Download](https://nodejs.org/)
- **npm** (comes with Node.js)
- **OpenAI API Key** - [Get one here](https://platform.openai.com/api-keys)
- **SMTP Email Account** (Gmail, Outlook, SendGrid, etc.)

## 🚀 Installation & Setup

### Step 1: Clone or Download the Project

Navigate to the project directory:
```bash
cd "C:\Users\JC\OneDrive\Desktop\Curser Project\p2_Iphone Calculator"
```

### Step 2: Install Backend Dependencies

Navigate to the server directory and install dependencies:
```bash
cd server
npm install
```

This will install:
- `express` - Web server
- `cors` - CORS middleware
- `dotenv` - Environment variables
- `openai` - OpenAI API client
- `nodemailer` - Email sending

### Step 3: Configure Environment Variables

1. Copy the example environment file:
   ```bash
   # Windows PowerShell
   Copy-Item .env.example .env
   
   # Windows CMD
   copy .env.example .env
   
   # Mac/Linux
   cp .env.example .env
   ```

2. Open `server/.env` and fill in your credentials:

   ```env
   # Server Port (default: 3000)
   PORT=3000

   # OpenAI API Key (REQUIRED)
   OPENAI_API_KEY=sk-your-actual-api-key-here
   
   # Optional: Choose OpenAI model (default: gpt-4o-mini)
   # OPENAI_MODEL=gpt-4o-mini

   # Email Configuration (REQUIRED)
   # For Gmail:
   SMTP_HOST=smtp.gmail.com
   SMTP_PORT=587
   SMTP_SECURE=false
   SMTP_USER=your-email@gmail.com
   SMTP_PASS=your-app-password
   MAIL_FROM=your-email@gmail.com
   ```

### Step 4: Set Up Email (Gmail Example)

If using Gmail, you need to create an **App Password**:

1. Go to your [Google Account settings](https://myaccount.google.com/)
2. Enable 2-Step Verification
3. Go to [App Passwords](https://myaccount.google.com/apppasswords)
4. Generate an app password for "Mail"
5. Use this app password (not your regular password) in `SMTP_PASS`

**For other email providers:**
- **Outlook**: `smtp-mail.outlook.com`, port `587`
- **SendGrid**: Use their SMTP settings from your dashboard
- **Custom SMTP**: Configure according to your provider's documentation

### Step 5: Start the Server

From the `server` directory:
```bash
npm start
```

You should see:
```
Travel Itinerary server running at http://localhost:3000
```

### Step 6: Open the Application

Open your browser and navigate to:
```
http://localhost:3000
```

The server also serves the frontend files, so everything runs from one port.

## 💻 Usage

1. **Fill out the form** with your trip details:
   - Enter starting location and destination
   - Specify number of days and travelers
   - Set your budget
   - Choose mode of travel
   - Provide your email address
   - Add any additional preferences (optional)

2. **Click "Generate & Email Itinerary"**

3. **Wait for processing** - The AI will generate your personalized itinerary

4. **Check your email** - The itinerary will be sent to the provided email address (check spam folder if not in inbox)

## 🔌 API Documentation

### Endpoint: `POST /api/generate-itinerary`

Generates a travel itinerary and sends it via email.

**Request Body:**
```json
{
  "startingLocation": "New York, NY",
  "destination": "Paris, France",
  "numberOfDays": 7,
  "numberOfTravelers": 2,
  "budget": "$2000",
  "modeOfTravel": "flight",
  "email": "user@example.com",
  "additionalPreferences": "Vegetarian food, prefer museums"
}
```

**Success Response (200):**
```json
{
  "success": true,
  "message": "Your itinerary has been generated and sent to your email. Check your inbox (and spam folder)."
}
```

**Error Response (400/500):**
```json
{
  "success": false,
  "error": "Error message here"
}
```

### Endpoint: `GET /api/health`

Check server status and configuration.

**Response:**
```json
{
  "ok": true,
  "openai": true,
  "email": true
}
```

## 📄 File Descriptions

### Frontend Files

- **`index.html`**: 
  - Main HTML structure
  - Form with all required and optional fields
  - Semantic HTML5 elements
  - Accessibility attributes (ARIA labels, roles)

- **`style.css`**: 
  - Modern dark theme styling
  - Responsive design for mobile and desktop
  - Smooth animations and transitions
  - CSS custom properties for theming

- **`Script.js`**: 
  - Form validation (client-side)
  - API communication with backend
  - Error handling and user feedback
  - Loading states and success messages

### Backend Files

- **`server/index.js`**: 
  - Express server setup
  - API route handlers
  - OpenAI integration for itinerary generation
  - Email sending via Nodemailer
  - Input validation
  - Error handling

- **`server/package.json`**: 
  - Node.js project configuration
  - Dependencies list
  - Scripts for running the server

- **`server/.env.example`**: 
  - Template for environment variables
  - Documentation for required configuration

## 🐛 Troubleshooting

### Server won't start
- **Check Node.js version**: Run `node --version` (should be 18+)
- **Verify dependencies**: Run `npm install` in the `server` directory
- **Check port availability**: Ensure port 3000 is not in use

### OpenAI errors
- **Invalid API key**: Verify your `OPENAI_API_KEY` in `.env`
- **Rate limits**: Check your OpenAI account usage limits
- **Model availability**: Ensure the specified model is available in your OpenAI account

### Email not sending
- **SMTP credentials**: Verify all SMTP settings in `.env`
- **Gmail App Password**: Make sure you're using an App Password, not your regular password
- **Firewall/Network**: Check if your network allows SMTP connections
- **Provider limits**: Some email providers have sending limits

### Form validation errors
- **Check browser console**: Open DevTools (F12) to see JavaScript errors
- **API connection**: Ensure the backend server is running
- **CORS issues**: The server includes CORS middleware, but check browser console for errors

### Itinerary not received
- **Check spam folder**: Emails might be filtered
- **Verify email address**: Ensure the email address is correct
- **Check server logs**: Look at the terminal where the server is running for errors

## 🔒 Security Notes

- **Never commit `.env` file**: It contains sensitive credentials
- **Use App Passwords**: For Gmail, always use App Passwords, not your main password
- **API Key Security**: Keep your OpenAI API key secure and don't share it
- **Rate Limiting**: Consider adding rate limiting for production use
- **Input Sanitization**: The backend validates inputs, but consider additional sanitization for production

## 🚀 Deployment

For production deployment:

1. **Environment Variables**: Set all environment variables on your hosting platform
2. **HTTPS**: Use HTTPS for secure connections
3. **CORS**: Configure CORS to allow only your frontend domain
4. **Rate Limiting**: Add rate limiting to prevent abuse
5. **Error Logging**: Set up proper error logging and monitoring
6. **Email Service**: Consider using a dedicated email service (SendGrid, Mailgun) for better deliverability

## 📝 License

This project is open source and available for personal and commercial use.

## 🤝 Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## 📧 Support

For issues or questions:
1. Check the Troubleshooting section above
2. Review server logs for error messages
3. Verify all environment variables are set correctly

---

**Happy Travel Planning! ✈️🗺️**
