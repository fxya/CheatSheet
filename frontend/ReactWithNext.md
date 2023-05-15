# React and Next.js Cheat Sheet

### Functional Components with Props
```typescript
import React from 'react';

type Props = {
  name: string;
  age: number;
};

const Person: React.FC<Props> = ({ name, age }) => {
  return (
    <div>
      <h1>{name}</h1>
      <p>{age} years old</p>
    </div>
  );
};

export default Person;
```
- This code defines a functional component `Person` that receives `name` and `age` as props of type `string` and `number` respectively.

### useState Hook
```typescript
import React, { useState } from 'react';

const Counter: React.FC = () => {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;
```
- The `useState` hook allows you to add state to functional components. In this example, a counter component is created, and `count` and `setCount` are used to manage the state.

### useEffect Hook
```typescript
import React, { useEffect } from 'react';

const DataFetcher: React.FC = () => {
  useEffect(() => {
    // Fetch data from an API
    // Runs after the component is rendered
    fetchData();
  }, []);

  return <div>Data Fetcher</div>;
};

export default DataFetcher;
```
- The `useEffect` hook is used for side effects in functional components. In this example, the effect is fetching data from an API, and the empty dependency array `[]` ensures that the effect runs only once after the initial render.

### Next.js Dynamic Routes
```typescript
// pages/users/[id].tsx
import { useRouter } from 'next/router';

const UserPage: React.FC = () => {
  const router = useRouter();
  const { id } = router.query;

  return <div>User ID: {id}</div>;
};

export default UserPage;
```
- Next.js allows dynamic routes using square brackets `[]`. In this example, the page component is located at `pages/users/[id].tsx`, and the `id` parameter is accessed using `useRouter` from the `next/router` module.

### Server-side Rendering (SSR) with Next.js
```typescript
// pages/index.tsx
import { GetServerSideProps, NextPage } from 'next';

type Props = {
  serverData: string;
};

const Home: NextPage<Props> = ({ serverData }) => {
  return <div>{serverData}</div>;
};

export const getServerSideProps: GetServerSideProps<Props> = async () => {
  const serverData = 'Data fetched from the server';
  return {
    props: {
      serverData,
    },
  };
};

export default Home;
```
- Next.js provides server-side rendering capabilities. In this example, the `getServerSideProps` function is used to fetch data on the server and pass it as props to the component.

### Static Site Generation (SSG) with Next.js
```typescript
// pages/posts.tsx
import React from 'react';

type Post = {
  id: string;
  title: string;
};

type PostsPageProps = {
  posts: Post[];
};

const PostsPage: React.FC<PostsPageProps> = ({ posts }) => {
  return (
    <div>
      <h1>Posts</h1>
      <ul>
        {posts.map((post) => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </div>
  );
};

export const getStaticProps = async () => {
  const response = await fetch('https://api.example.com/posts');
  const posts: Post[] = await response.json();

  return {
    props: { posts },
  };
};

export default PostsPage;
```

