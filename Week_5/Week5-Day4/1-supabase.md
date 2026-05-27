# Adding a database!

🚨 Warning: when copying and pasting your file make sure that the imports match YOUR project structure. This will help avoid the little bugs on the way 🐜 🐜 🚨

We're going to connect your code to a database so we can save the chat history in your conversations, along with some other data.

For our database, we'll be using a database service called Supabase. Supabase is built on top of a popular open source database system called PostgreSQL (or just Postgres). Supabase is also a "hosted" service, which means we don't have to run a separate server to host it ourselves (which can be a pain). Supabase basically adds a hosting service and nice UI to the utilitarian power of Postgres.

## Setting up a Supabase database

1. Create an account on Supabase - https://supabase.com/
2. Create a new organization and a project (recommend calling the org "sea-yourname" and the project something like "chatbots")
3. Wait a few minutes for your database project to be created

## Connecting your app to Supabase

### Let go create some keys:

1. Go to https://app.supabase.com and log in.

2. Open your new supabase your project.

3. On the left sidebar, click ⚙️ Settings → API Keys.
   You’ll see something similar to this:
   <img src="./supaAPIKey.jpg">
   don't worry about putting these keys in your `.env.local`. The reason why we went looking for keys first is that they auto populate in our `connect` tab once we create them.
4. Select `Create new API Keys` and agree with the pop up window message
   <img src="./Supabase project..png">
   Once your project is created, we need to get some packages and the proper connection keys to help our app connect to Supabase!

### Adding the connection code to our project :

5. From the project dashboard, find the "Connect" button and click it  
   <img src="./supaConnect.jpg">
6. Select the "Mobile Frameworks" tab, then look at the three things below.
   <img src="./supaKeys.jpg">
   These are files that contain the connection keys and some example code! P.S look at the photo above and note the three arrows. We won't be using them exactly as written, but they're still very helpful. We'll walk through each of them separately.

### `.env.local`

For the `.env.local` file, we want to put our connection keys in our `.env.local` file. You should already have an environment variable file (aka `.env.local`) with your ChatGPT api key in it, so just add to that! If you don't have one, create one and add `.env.local` to your `.gitignore` file. Notice that this page does not expose your `EXPO_PUBLIC_SUPABASE_KEY` follows the steps to get get the key

### `utils/supabase.ts`

For the `utils/supabase.ts` file, we want that almost exactly as it, but your file should be called `supabase.js` instead of `supabase.ts`, because we're using JavaScript (`.js`), not TypeScript (`.ts`). _You can use AI to help you convert the file from Typescript to Javascript._

Note that this file imports some packages we don't have! Let's install them:

```bash
npx expo install @supabase/supabase-js @react-native-async-storage/async-storage react-native-url-polyfill
npx expo install expo-env
```

### `App.tsx`

For the `App.tsx` file example, we're going to do something a lil wild, so hold on to your socks. We're going to replace our whole `App.js` code with this example, **temporarily**, to check if our setup is working. Before continuing, make sure you've committed and pushed to github recently so you don't lose anything important! Once you're sure you've saved your work (and your socks are secured), copy paste the example code into `App.js`, replacing everything that's there. _You can use AI to help you convert the file from Typescript to Javascript._

When you do this, you'll hopefully get an error that looks like this:

<img src="./error.png" style="width: 50%; height: auto;">

## Addressing `errors fetching todos`

We're hoping for this error, because if you check out the code in `App.js`, it makes sense! Find this line:

```js
const { data: todos, error } = await supabase.from("todos").select();
```

This line tries to access a database table on supabase called "todos". But we don't have one!

So let's make one! From the supabase project dashboard, use the left sidebar to go to the "Table Editor", then find the green "Create a new table" button:

  <img width="1477" alt="Screen Shot 2024-07-17 at 3 36 08 PM" src="https://github.com/user-attachments/assets/947b05d7-6858-4705-a5a4-3b7f98590c84">

Now let's create a "todos" table, and add a text column called "title"

<img width="45%" alt="Screen Shot 2024-07-17 at 3 38 08 PM" src="https://github.com/user-attachments/assets/58a551cb-696e-439c-9eba-413c1f22d0d1"> <img width="45%" alt="Screen Shot 2024-07-17 at 4 48 03 PM" src="https://github.com/user-attachments/assets/6db1e8ce-b7fb-4f3f-99e9-e25f6007e47b">

<br>

Then we'll add some dummy data to that table

  <img alt="Screen Shot 2024-07-17 at 4 50 37 PM" src="https://github.com/user-attachments/assets/ae6fe89d-3a4d-4b2b-9dba-4c0126518584">

  <img alt="Screen Shot 2024-07-17 at 4 52 46 PM" src="https://github.com/user-attachments/assets/71191ed1-2983-4936-a901-c349487f7e19">

<br>

<br>

Now when we run it, we should see the dummy data from your database in your app!

  <img width="400" src="https://github.com/user-attachments/assets/ff715d6a-2306-43a3-b032-e0dd32c288eb">

## Fin!

<br>

<br>

<br>

<br>
