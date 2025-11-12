n## Upvote

Upvote is a Reddit-esque web application that allows users to create posts, upvote and downvote posts, and comment on posts in a multi-threaded, nested list.

The project is built using Next.js with the /app router and [Tailwind CSS](https://tailwindcss.com/), and uses [Auth.js (formerly Next Auth)](https://authjs.dev/) for user authentication. The data is stored in a Postgres database, which is created and accessed with raw SQL queries using the `pg` package.

The project is a work in progress and is not yet complete.

## Features

- [x] View a list of posts
- [x] View a single post
- [x] Create a post
- [x] Upvote and downvote posts
- [x] Pagination of posts
- [x] Comment on posts
- [x] Nested comments (recursive lists)
- [x] User authentication

## Setup instructions

1. Fork the repository (check "copy the main branch only") and clone your fork to your local machine
2. Run `npm install`
3. Create a `.env.local` file in the root directory and add the following environment variables:
   - `DATABASE_URL` - the URL of your Postgres database (e.g., the Supabase connection string)
   - `NEXTAUTH_SECRET` - the NextAuth secret string (this can be anything at all like a password, but keep it secret!)
   - `GITHUB_ID` - the GitHub OAuth client ID (create yours in [Github developer settings](https://github.com/settings/developers))
   - `GITHUB_SECRET` - the GitHub OAuth client secret (create this in [Github developer settings](https://github.com/settings/developers))
4. Create the database schema by running the SQL commands in `schema.sql` in your database (e.g., by running the commands in Supabase Query Editor)
5. Run `npm run dev` to start the development server
6. Open [http://localhost:3000](http://localhost:3000) with your browser to see the site

## Assignment Reflection

### Requirements Met & Goals Achieved

- Joined an existing project and quickly onboarded by reviewing the codebase and documentation.
- Deployed the app to Vercel, configuring all required environment variables for production.
- Fixed the issue allowing users to vote multiple times on the same post by adding a unique constraint to the `votes` table in the SQL schema and confirming the in-app logic prevents duplicate votes.

### Requirements Not Fully Achieved

- Did not implement TipTap for rich text editing (stretch goal).
- Did not address all stretch goals (e.g., user profiles, moderation tools, etc.) due to time constraints.

### Challenges & Reflections

- The main challenge was adapting to the new NextAuth beta, as documentation is still evolving and some setup steps were unclear or outdated. Careful reading of the latest docs and community resources was essential.
- Joining an existing project required quickly understanding the code structure and database relationships, especially for recursive/nested comments and vote logic.
- Deploying to Vercel was straightforward once environment variables were set correctly. The main pitfall was ensuring secrets were not committed to git and were set in the Vercel dashboard.

### What Went Well / What Could Be Improved

- The recursive comment system and pagination features worked as expected and were easy to extend.
- The main improvement would be to add more robust error handling for authentication and voting, and to implement richer text editing for posts and comments.

### Useful Resources

- [NextAuth.js Beta Documentation](https://authjs.dev/)
- [GitHub OAuth App Setup Guide](https://www.youtube.com/watch?v=H-1ozULYdyc)
- [Vercel Deployment Docs](https://vercel.com/docs)

### Feedback

I would appreciate feedback on my approach to onboarding and improving an existing codebase, as well as suggestions for further stretch goals or best practices for production deployment.

## Potential future features

- [ ] User profiles
- [ ] Sorting posts by recent (date posted), top (most upvotes), and most controversial (most upvotes _and_ downvotes)
- [ ] User karma scores
- [ ] User badges / trophies (awards for achievements like number of posts, years on the site, etc.)
- [ ] User settings (eg. number of posts per page, theme, etc.)
- [ ] Moderation tools / reporting or flagging objectionable comments for removable by admins
- [ ] Searching posts (possibly using simple SQL LIKE '%some search%', or [Postgres text search](https://www.crunchydata.com/blog/postgres-full-text-search-a-search-engine-in-a-database))
- [ ] Subreddits (separate communities, that isn't just one big list of posts, that can be created by users)
- [ ] User notifications
- [ ] User private messaging
- [ ] User blocking
- [ ] User following
- [ ] User feed (posts from users you follow)
- [ ] User flair
