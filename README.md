# ROI Campaign Tracker

A modern web application for tracking and analyzing marketing campaign ROI (Return on Investment) built with React, TypeScript, and Supabase.

## Features

- 📊 **Campaign Management**: Add, view, and delete marketing campaigns
- 💰 **ROI Calculation**: Automatic ROI calculation based on cost and revenue
- 📈 **Analytics Dashboard**: Visual charts showing ROI trends and cost vs revenue
- 🎨 **Modern UI**: Clean, responsive design with Tailwind CSS
- 🔒 **Data Persistence**: Secure data storage with Supabase
- ⚡ **Real-time Updates**: Instant updates across all components

## Tech Stack

- **Frontend**: React 18, TypeScript, Vite
- **Styling**: Tailwind CSS
- **Charts**: Recharts
- **Database**: Supabase (PostgreSQL)
- **Deployment**: Ready for Vercel/Netlify

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm or yarn
- Supabase account

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd roi-campaign-tracker
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Update `.env` with your Supabase credentials:
   ```
   VITE_SUPABASE_URL=https://your-project.supabase.co
   VITE_SUPABASE_ANON_KEY=your-anon-key
   ```

4. **Set up the database**
   - Go to your Supabase dashboard
   - Navigate to SQL Editor
   - Run the SQL from `supabase/schema.sql`

5. **Start the development server**
   ```bash
   npm run dev
   ```

6. **Open your browser**
   Navigate to `http://localhost:5173`

## Usage

### Adding a Campaign
1. Fill in the campaign name, cost, and revenue
2. Click "Add Campaign" - ROI is calculated automatically
3. The campaign appears in the list and analytics update instantly

### Viewing Analytics
- **Summary Cards**: Quick overview of total campaigns, costs, revenue, and average ROI
- **ROI Over Time**: Line chart showing ROI trends
- **Cost vs Revenue**: Bar chart comparing costs and revenue by campaign

### Managing Campaigns
- View all campaigns in chronological order
- Delete campaigns with confirmation
- See formatted currency and dates

## Project Structure

```
src/
├── components/           # React components
│   ├── CampaignForm.tsx     # Form for adding campaigns
│   ├── CampaignList.tsx     # List of all campaigns
│   └── CampaignAnalytics.tsx # Analytics dashboard
├── services/            # External services
│   └── supabaseClient.ts    # Supabase configuration
├── types/               # TypeScript type definitions
│   └── Campaign.ts          # Campaign interface
├── App.tsx              # Main app component
├── main.tsx             # App entry point
└── index.css            # Global styles
```

## Available Scripts

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

## Database Schema

The app uses a single `campaigns` table:

```sql
CREATE TABLE campaigns (
  id BIGSERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  cost DECIMAL(10,2) NOT NULL CHECK (cost >= 0),
  revenue DECIMAL(10,2) NOT NULL CHECK (revenue >= 0),
  roi DECIMAL(5,2) NOT NULL,
  timestamp TIMESTAMPTZ NOT NULL,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  updated_at TIMESTAMPTZ DEFAULT NOW()
);
```

## Deployment

### Vercel
1. Push your code to GitHub
2. Connect your repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy!

### Netlify
1. Build the project: `npm run build`
2. Deploy the `dist` folder to Netlify
3. Add environment variables in Netlify dashboard

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Commit your changes: `git commit -am 'Add feature'`
4. Push to the branch: `git push origin feature-name`
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

If you have any questions or run into issues, please open an issue on GitHub.