Tasks:
1. Identify and fix issues where data is not validated or checked before it gets used
there are no SQL injections
    No findings. A quick review shows no SQL‑injection vulnerabilities in the queries.

2. Identify and fix poor database queries and poor data loading patterns
while not much of an issue with local sqlite, implement correct indexes
    Step 1: pnpm drizzle-kit studio to create an index on table posts and named: posts_author_id_idx
    Step 2: Then optimized to drizzle config file: 
            CREATE INDEX `posts_author_id_idx` ON `posts` (`author_id`);
    Step 3: Finnaly, I relized this is orm, it should be in schema, so it is:
            table => [index('posts_author_id_idx').on(table.authorId)]
            pnpm npx npx drizzle-kit push
    Summary: I haven't used Drizzle before, but it is quite similar to Prisma.

3. Identify and fix poor React performance
