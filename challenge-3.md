# 🌱 Challenge III: Display data on the frontend using The Graph

## Description

Create a React app and display data using the subgraph

## Rewards

We can’t wait for you to complete this and claim, **your PFP’s 🖼️** and **$GRT**

## Hashtags Used

- [ ] `#graphathon`
- [ ] `#graphIndia`

## Steps on how to Contribute?

 - Create a folder/directory and open it in your code editor.

 - We will create a React app. Open your terminal pointing towards the directory and run the following command
  ```
  npm create vite@latest
  ```
 - Enter the Project Name as `frontend` or `client`.
 - Select `React` as the framework and then select `JavaScript` (without SWC ❌).
 - Run the following commands to start. (You can refer to your terminal)
  ```
  cd client
  ```
  ```
  npm install
  ```
  ```
  npm run dev
  ```

 - We will also need to install `graphql` to query the data and `urql` which is a highly customizable and versatile GraphQL client for React.
  ```
  npm install graphql urql@3.0.3
  ```

 - Inside the directory, go to the `src/App.jsx` and replace the existing code with
  ```javascript
  import { useState, useEffect } from 'react';
  import './App.css';
  
  function App() {
    return (
      <>
        <div>
  
        </div>
      </>
    )
  }

  export default App;
  ```

 - We are going to make use of the Uniswap subgraph for this challenge. See it [here](https://thegraph.com/explorer/subgraphs/ELUcwgpm14LKPLrBRuVvPvNKHQ9HvwmtKgKSH6123cr7?view=Overview&chain=mainnet).
  
 - Click on `Query` button on the right and copy the Query URL to access the subgraph.

 - Go back to our `App.jsx` and store the URL in a variable inside the App function.
```javascript
const QueryURL = "https://gateway.thegraph.com/api/[api-key]/subgraphs/id/ELUcwgpm14LKPLrBRuVvPvNKHQ9HvwmtKgKSH6123cr7"
```
 - You need an API Key to query the data. Under the Query URL you can see the option to `Manage API Keys`. Click on that and it will take you to create it. You can also create it using [this](https://thegraph.com/studio/apikeys/) link.
 - <img width="435" alt="Screenshot 2023-07-04 at 1 20 04 PM" src="https://github.com/TheGraphIndia/Graph-A-Thon/assets/47234407/81f2507f-c1fe-4eaa-a1c4-44386746502e">

 - Click on `Create API Key` and enter a name eg. graphathon-uniswap.
 - You get 1,000 free queries for the API key. Enter your email address and claim your queries.
 - Copy the generated API key and paste it into our query URL.

 - Add the data you want to query below the `QueryURL` variable. Here we will get the data about the first 5 token details of Uniswap.
```javascript
const query = `{
  tokens(first: 5) {
    id
    name
    symbol
    decimals
  }
}`
```

 - Create a client to access Uniswap. We will make of `urql` for this. Add the following import statement at the top
```javascript
import { createClient } from 'urql';
```

 - To create the client add the following code after the `query` variable
```javascript
const client = createClient({
  url: QueryURL
})
```

 - We will make use of useEffect and useState to track the state. Add the following code in the App function
```javascript
const [tokens, setTokens] = useState([]);
```
```javascript
useEffect(() => {
  const getTokens = async () => {
    const { data } = await client.query(query).toPromise();
    console.log(data);
    setTokens(data.tokens);
  }
  getTokens();
}, [])
```

 - To display the data on the frontend, we will return the following.
```javascript
return (
    <>
      <div>
        <h1>Tokens Information</h1>
        {tokens !== null && tokens.length > 0 && tokens.map((token) => {
          return (
            <div key={token.id}>
              <div>{token.id}</div>
              <div>{token.name}</div>
            </div>
          );
        })}
      </div>
    </>
  );
```

 - Your final `App.jsx` should look like follows -:
```javascript
import { useEffect, useState } from 'react';
import { createClient } from 'urql';
import './App.css';

function App() {
  const [tokens, setTokens] = useState([]);

  const QueryURL = "https://gateway.thegraph.com/api/[api-key]/subgraphs/id/ELUcwgpm14LKPLrBRuVvPvNKHQ9HvwmtKgKSH6123cr7";

  const client = createClient({
    url: QueryURL
  });

  const query = `{
    tokens(first: 5) {
      id
      name
      symbol
      decimals
    }
  }`

  useEffect(() => {
    const getTokens = async () => {
      const { data } = await client.query(query).toPromise();
      setTokens(data.tokens);
    };
    getTokens();
  }, []);

  return (
    <>
      <div>
        <h1>Tokens Information</h1>
        {tokens !== null && tokens.length > 0 && tokens.map((token) => {
          return (
            <div key={token.id}>
              <div>{token.id}</div>
              <div>{token.name}</div>
            </div>
          );
        })}
      </div>
    </>
  );
}

export default App;
```

 - Run `npm run dev` to view the frontend.

 - Wohooo! You did it. 🥳 Congratulationssss! Share it with the world.

 - Make use of The Graph Playground to use different queries and display that data. (SKY IS THE LIMIT 🌌)

 - Create a new file with the title `solution-3.md` and add the frontend screenshot in the file.

 - **[🚨VERY IMPORTANT STEP🚨]**  Submit the link of this `solution-3.md` file to this [Graph-A-Thon challenge submission form](https://airtable.com/).
 
 
 (ex: https://github.com/username/Graph-Advocates--Graph-A-Thon-2023/blob/username_graphathon/solution-3.md)

-------
 
## Submission Guidelines

- Create a new branch `username_graphathon`, e.g. `yash251_graphathon`

- Create a file named `solution-3.md` for this challenge. 

- Add the frontend screenshot in the file.

- Submit details on the [**Airtable form**](https://airtable.com/).

-------

[**Submission Challenge III form**](https://airtable.com/)

*This is an important step, please don't skip it.*
