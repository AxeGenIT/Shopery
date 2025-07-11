# Shopery Server

A robust Node.js backend server built with Express.js and TypeScript, providing a comprehensive e-commerce API for the Shopery application.

## 🚀 Features

- **TypeScript**: Full TypeScript implementation for type safety and better development experience
- **Express.js**: Fast and minimal web framework for Node.js
- **MongoDB**: Database integration using Mongoose ODM
- **Authentication**: JWT-based authentication with refresh tokens
- **File Upload**: Cloudinary integration for image management
- **Email Service**: Nodemailer integration for email functionality
- **Input Validation**: Zod schema validation for request data
- **Error Handling**: Comprehensive error handling with custom error classes
- **Security**: CORS, cookie parser, and other security middleware
- **Code Quality**: ESLint and Prettier for code formatting and linting

## 📋 Prerequisites

Before running this project, make sure you have the following installed:

- Node.js (v18 or higher)
- npm or yarn
- MongoDB database
- Cloudinary account (for image uploads)

## 🛠️ Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/AxeGenIT/-Shopery.git
   cd Shopery/server
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Environment setup**
   Create a `.env` file in the server root directory and configure the following variables:

   ```env
   NODE_ENV=development
   PORT=5000
   DB_URL=your_mongodb_connection_string

   # JWT Configuration
   JWT_ACCESS_SECRET=your_jwt_access_secret
   JWT_ACCESS_EXPIRES_IN=15m
   JWT_REFRESH_SECRET=your_jwt_refresh_secret
   JWT_REFRESH_EXPIRES_IN=7d
   JWT_OTP_SECRET=your_jwt_otp_secret
   JWT_PASS_RESET_SECRET=your_jwt_password_reset_secret
   JWT_PASS_RESET_EXPIRES_IN=10m

   # Bcrypt Configuration
   BCRYPT_SALT_ROUNDS=12

   # Admin Configuration
   ADMIN_EMAIL=admin@example.com
   ADMIN_PASSWORD=admin_password
   ADMIN_PROFILE_PHOTO=admin_photo_url

   # Cloudinary Configuration
   CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
   CLOUDINARY_API_KEY=your_cloudinary_api_key
   CLOUDINARY_API_SECRET=your_cloudinary_api_secret

   # Email Configuration
   EMAIL_HOST=your_email_host
   EMAIL_PORT=587
   EMAIL_USER=your_email_user
   EMAIL_PASS=your_email_password
   ```

## 🏃‍♂️ Running the Application

### Development Mode

```bash
npm run dev
```

This will start the server in development mode with hot reloading using ts-node-dev.

### Production Mode

```bash
# Build the project
npm run build

# Start the production server
npm start
```

## 📁 Project Structure

```
server/
├── src/
│   ├── app.ts                 # Express application setup
│   ├── server.ts              # Server entry point
│   └── app/
│       ├── builder/           # Query builder utilities
│       │   └── QueryBuilder.ts
│       ├── config/            # Configuration files
│       │   ├── index.ts       # Main config
│       │   ├── cloudinary.config.ts
│       │   └── multer.config.ts
│       ├── DB/                # Database utilities
│       │   └── seed.ts        # Database seeding
│       ├── errors/            # Custom error handlers
│       │   ├── appError.ts
│       │   ├── handleCastError.ts
│       │   ├── handleDuplicateError.ts
│       │   ├── handleValidationError.ts
│       │   └── handleZodError.ts
│       ├── interface/         # TypeScript interfaces
│       │   ├── error.ts
│       │   ├── IImageFile.ts
│       │   ├── index.d.ts
│       │   └── user.ts
│       ├── middleware/        # Express middleware
│       │   ├── auth.ts
│       │   ├── bodyParser.ts
│       │   ├── clientInfoParser.ts
│       │   ├── globalErrorHandler.ts
│       │   ├── notFound.ts
│       │   └── validateRequest.ts
│       ├── modules/           # Feature modules
│       │   ├── Auth/          # Authentication module
│       │   │   ├── Auth.controller.ts
│       │   │   ├── Auth.interface.ts
│       │   │   ├── Auth.model.ts
│       │   │   ├── Auth.routes.ts
│       │   │   ├── Auth.service.ts
│       │   │   └── Auth.validation.ts
│       │   └── User/          # User management module
│       │       ├── User.controller.ts
│       │       ├── User.interface.ts
│       │       ├── User.model.ts
│       │       ├── User.routes.ts
│       │       ├── User.service.ts
│       │       └── User.validation.ts
│       ├── routes/            # API routes
│       │   └── index.ts
│       └── utils/             # Utility functions
│           ├── catchAsync.ts
│           ├── emailHelper.ts
│           ├── generateOrderInvoicePDF.ts
│           ├── generateOtp.ts
│           └── sendResponse.ts
├── scripts/                   # Build and utility scripts
│   └── create-module.ts       # Module generator script
├── types/                     # Type definitions
│   └── sslcommerz-lts.d.ts   # SSL Commerce types
├── uploads/                   # File upload directory
├── package.json
├── tsconfig.json
├── eslint.config.mjs
└── README.md
```

## 🔧 Available Scripts

- `npm run dev` - Start development server with hot reloading
- `npm run build` - Build the TypeScript project
- `npm start` - Start the production server
- `npm run lint` - Run ESLint to check code quality
- `npm run lint:fix` - Fix ESLint errors automatically
- `npm run format` - Format code using Prettier
- `npm test` - Run tests (not implemented yet)

## 🌐 API Endpoints

The server exposes the following API endpoints:

### Base URL

```
http://localhost:5000/api/v1
```

### Available Routes

- **User Management**: `/api/v1/user/*`
- **Authentication**: `/api/v1/auth/*` (to be implemented)

### Health Check

- **GET** `/` - Server health check and system information

## 🔒 Authentication

The application uses JWT (JSON Web Tokens) for authentication with:

- Access tokens (short-lived, 15 minutes)
- Refresh tokens (long-lived, 7 days)
- OTP tokens for verification
- Password reset tokens

## 📝 Module Structure

Each feature module follows a consistent structure:

- **Controller**: Handles HTTP requests and responses
- **Service**: Contains business logic
- **Model**: Mongoose schema and model definition
- **Interface**: TypeScript type definitions
- **Routes**: API route definitions
- **Validation**: Zod schema validation

## 🛡️ Error Handling

The application includes comprehensive error handling:

- Global error handler middleware
- Custom error classes
- Specific handlers for MongoDB errors (Cast, Duplicate, Validation)
- Zod validation error handling

## 📤 File Upload

File upload functionality using:

- **Multer**: For handling multipart/form-data
- **Cloudinary**: For cloud storage and image optimization

## 📧 Email Service

Email functionality powered by Nodemailer for:

- User verification emails
- Password reset emails
- Order confirmations
- Other transactional emails

## 🔍 Query Builder

Advanced query building capabilities for:

- Searching and filtering
- Sorting and pagination
- Field selection
- Population of related data

## 🚀 Deployment

### Production Checklist

1. Set `NODE_ENV=production` in environment variables
2. Configure production database URL
3. Set secure JWT secrets
4. Configure email service for production
5. Set up Cloudinary for production
6. Build the project: `npm run build`
7. Start the server: `npm start`

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📋 Development Guidelines

- Follow TypeScript best practices
- Use ESLint and Prettier for code formatting
- Write meaningful commit messages
- Create comprehensive tests for new features
- Document API endpoints
- Follow RESTful API conventions

## 🐛 Known Issues

- Tests are not implemented yet
- Some modules may need additional validation
- SSL Commerce integration is in progress

## 📞 Support

For support and questions:

- GitHub Issues: [Project Issues](https://github.com/AxeGenIT/-Shopery/issues)
- Repository: [Shopery](https://github.com/AxeGenIT/-Shopery)

## 📄 License

This project is licensed under the ISC License.

---

**Happy coding! 🚀**
