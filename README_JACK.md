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
            pnpm npx drizzle-kit push
    Summary: I haven't used Drizzle before, but it is quite similar to Prisma.

3. Identify and fix poor React performance
    Not perfect, just use react-virtual to achive a list component. Some idea:
    - Multiple React libraries can implement virtual lists, e.g., react-window, react-virtualized, @tanstack/react-virtual.
    - Parameter searchTerm is necessary for highlighting and doesn’t add extra render cost; no need for extra leaf components.
    - For large data, server-side pagination is best for true infinite scrolling.
    - Under ~10k items, client-side pagination suffices; DOM nodes, not data size, drive performance and make grid layouts easier.

4. Refactor the registerUser function using Effect.
this doesn't need to be perfect, nor use the full Effect toolbox. just a basic understanding of what Effect provides
    This is the most easy one, Effect is a function programming lib like fp-ts, I just use AI to generate an initial function, and then fine-tune it.
