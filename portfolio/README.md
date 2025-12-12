# AI Portfolio Builder

A full SaaS platform for creating professional portfolios using AI, built with modern 2025 technologies.

## 🚀 Quick Start

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Set up environment variables:**
   Copy `.env.example` to `.env.local` and fill in your API keys:
   ```bash
   cp .env.example .env.local
   ```

3. **Run the development server:**
   ```bash
   npm run dev
   ```

4. Open [http://localhost:3000](http://localhost:3000) in your browser.

## 🔧 Required API Keys

Before the app is fully functional, you need to set up these services:

### MongoDB Atlas
1. Create a free cluster at [MongoDB Atlas](https://cloud.mongodb.com)
2. Create a database user and get your connection string
3. Add to `.env.local`: `MONGODB_URI="your_connection_string"`

### Clerk Authentication
1. Create an app at [Clerk.com](https://clerk.com)
2. Get your publishable and secret keys
3. Add to `.env.local`:
   - `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY="pk_test_..."`
   - `CLERK_SECRET_KEY="sk_test_..."`

### Stripe Payments
1. Create an account at [Stripe.com](https://stripe.com)
2. Get your test API keys
3. Add to `.env.local`:
   - `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY="pk_test_..."`
   - `STRIPE_SECRET_KEY="sk_test_..."`

### OpenAI
1. Get an API key from [OpenAI](https://platform.openai.com/api-keys)
2. Add to `.env.local`: `OPENAI_API_KEY="sk-..."`

## 📁 Project Structure

```
portfolio/
├── src/
│   ├── app/              # Next.js App Router pages
│   │   ├── (auth)/       # Authentication pages (Clerk)
│   │   ├── (dashboard)/  # Protected dashboard pages
│   │   ├── api/          # API routes
│   │   └── p/            # Public portfolio pages
│   ├── components/       # React components
│   │   ├── ui/           # Shadcn UI components
│   │   └── landing/      # Landing page components
│   ├── lib/              # Utility libraries
│   │   ├── db/           # MongoDB models
│   │   ├── ai/           # OpenAI integration
│   │   └── stripe/       # Stripe integration
│   ├── locales/          # i18n translation files
│   ├── types/            # TypeScript types
│   └── validations/      # Zod schemas
```

## ✨ Features

- **AI Portfolio Generation** - Generate complete portfolios from descriptions
- **Real-time Editor** - Edit sections with AI assistance
- **Multiple Themes** - Choose from beautiful templates
- **Analytics** - Track portfolio views
- **Subscription System** - Free and Premium tiers
- **Multi-language** - English and Arabic with RTL support
- **SEO Optimized** - Server-side rendered public pages

## 🛠 Tech Stack

- **Framework:** Next.js 15 (App Router)
- **Styling:** Tailwind CSS + Shadcn UI
- **Database:** MongoDB with Mongoose
- **Auth:** Clerk
- **Payments:** Stripe
- **AI:** OpenAI GPT-4
- **Validation:** Zod
- **Language:** TypeScript

## 📜 Scripts

```bash
npm run dev        # Start development server
npm run build      # Build for production
npm run start      # Start production server
npm run lint       # Run ESLint
npm run storybook  # Start Storybook
```

## 📄 License

MIT License - feel free to use for your own projects!
