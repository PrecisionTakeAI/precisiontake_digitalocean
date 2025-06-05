# PrecisionTakeAI - Automated Plumbing Design Estimation

PrecisionTakeAI is an advanced AI-powered solution for automating plumbing design estimation. The system analyzes plumbing design PDFs, detects elements, handles multi-page duplication, verifies compliance with regional standards, and generates accurate cost estimations.

## Features

- **PDF Processing**: Extract and analyze plumbing designs from PDF files
- **Element Detection**: Identify pipes, valves, fixtures, and other plumbing elements
- **Multi-Page Handling**: Intelligently detect and reconcile duplicate elements across multiple pages
- **Regional Compliance**: Verify designs against plumbing codes from multiple regions
- **Cost Estimation**: Generate accurate material and labor cost estimates
- **Itemized Output**: Export detailed spreadsheets with cost breakdowns

## Technology Stack

- **Backend**: Node.js with Express and TypeScript
- **Frontend**: React with shadcn/ui components and TanStack Query
- **Database**: PostgreSQL with Drizzle ORM
- **Authentication**: Passport.js with session-based auth
- **PDF Processing**: PDF.js and custom vectorization algorithms
- **AI Detection**: TensorFlow.js for element recognition

## Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL 14+
- npm or yarn

### Environment Variables

Create a `.env` file in the root directory with the following variables:

```
# Server
PORT=3000
NODE_ENV=production

# Database
DATABASE_URL=postgresql://username:password@localhost:5432/precisiontake

# Authentication
SESSION_SECRET=your-session-secret

# PDF Processing
PDF_PROCESSING_TIMEOUT=300000
```

### Installation

1. Clone the repository
2. Install dependencies:
   ```
   npm install
   ```
3. Set up the database:
   ```
   npm run db:migrate
   ```
4. Build the application:
   ```
   npm run build
   ```
5. Start the server:
   ```
   npm start
   ```

## Deployment

This application is configured for deployment on DigitalOcean App Platform. See the [deployment guide](DEPLOYMENT.md) for detailed instructions.

## License

This project is proprietary software. All rights reserved.

## Support

For support, please contact support@precisiontake.ai
