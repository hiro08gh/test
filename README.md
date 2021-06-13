# raect-cache-fetch

Simple cache helper for data fetch.

## Install

```bash
$ npm install --save react-cache-fetch
```

## Usage

First, create fetcher functions.

```typescript
const fetcher = (url: string) = fetch(url).then((res) => res.json());
```

and, using useCacheFetch api.

```typescript
import React from "react";
import { useCacheFetch } from "raect-cache-fetch";

const App: React.VFC<> = () => {
  const [data, loading, error] = useCacheFetch(["key"], fetcher("/api/data"), 100);

  if (loading) {
    return <div>Loading...</div>;
  }

  if (error) {
    return <div>Error</div>;
  }

  return (
    <div>
      {data.map((res) => (
        <div key={res.id}>{res.title}</div>
      ))}
    </div>
  );
};
```
