# Authentication!

Earlier, you went through the first few steps of connecting Supabase to your app, but there were a few big caveats.
 * Remember that RLS (Row Level Security) thing we told you to disable? Well, leaving that disabled means that anyone (who knows the right commands) can read/edit/delete the stuff in our table!
 * Our simple UI only let us view/read the data in our database, but we couldn't change anything!

For this milestone, we're going to set up an account system and authentication! This will let us secure to our database (by configuring which users can read/edit/delete things)

We'll be [following this tutorial](https://supabase.com/docs/guides/getting-started/tutorials/with-expo-react-native) pretty closely, but with a few tweaks.

## Creating the User Profiles table

Our database needs a place to store information about our users! We're going to create a "Profiles" page using a "schema" template from Supabase. 

*A "schema" is a pattern the database follows, e.g. "each user must have an id, a username, and a display name"*

1. On the Supabase dashboard, go to the "SQL Editor" tab on the left sidebar
   
2. From the SQL Editor page, choose "Quickstarts" then click "User Management Starter"

3. Click the green "Run" button to execute the query.  
  *This is a SQL query! It creates a new table, defines the columns the table will have, sets the security policies for the table, and a few other things*

5. Now, go to the "Table Editor" tab and you should see you now have two tables available: "profiles" (new!) and "todos". Check out the "profiles" table, and you should see that it has no data but does have columns like `id`, `username` and `full_name`

## Building the app

We want you to learn about working through the hiccups of documentation, so for the next few sections, you'll be working off of the documentation, but with a few hints from us here. 

The headings below will match the names of the headings in the documentation:

https://supabase.com/docs/guides/getting-started/tutorials/with-expo-react-native#building-the-app

### Initialize a React Native App

https://supabase.com/docs/guides/getting-started/tutorials/with-expo-react-native#initialize-a-react-native-app

 * We don't need most of the stuff here! We did a lot of it in the milestone earlier.
 * Do we have an expo app already?
 * We already have some of the packages, but expo won't install packages we already have. (You may need to install `@rneui/base` to fix another error, but cross that bridge when you get to it!)
 * Do we have something like a `supabase.ts` file already?

### Setup a login component

https://supabase.com/docs/guides/getting-started/tutorials/with-expo-react-native#set-up-a-login-component

 * Remember that our files need to end in `.js`, not `.tsx`.
 * Can you spot the other import error we'll run into? Don't worry if not, the error message you'll run into later makes it easy to spot

### Account Page

https://supabase.com/docs/guides/getting-started/tutorials/with-expo-react-native#account-page

This file has some weird typescript stuff in it, here's how to fix them
 * Close to the top, you'll see this syntax:
  ```js
  export default function Account({ session }: { session: Session }) {
  ```
  Change it to this:
  ```js
  export default function Account({ session }) {
  ```
 * The `updateProfile` function also has some weirdness:

  ```ts
  async function updateProfile({
    username,
    website,
    avatar_url,
  }: {
    username: string
    website: string
    avatar_url: string
  }) {
  ```

  Change it to this:
  ```js
  async function updateProfile({
    username,
    website,
    avatar_url,
  }) {
  ```

 * There will also be a very similar small import error here. Again, you'll find it when you run into the error.

### Launch!

https://supabase.com/docs/guides/getting-started/tutorials/with-expo-react-native#launch

We're going to replace `App.js` again! There's a bit more weird typescript thing to fix

Replace this line:
```ts
const [session, setSession] = useState<Session | null>(null)
```
With this:
```js
const [session, setSession] = useState(null)

```

## Run the app and fix errors!

Even if you followed the documentation and these hints perfectly, I still left a few errors for you to find and fix yourself! Documentation is never perfect, just read the error messages and make educated guesses! 

Also, instead of just sharing the fix with your peers, point them towards the part of the error message that helped you figure it out.

Your goal is to get to this screen without any errors showing up:

<img width="50%" src="https://github.com/user-attachments/assets/41d2a706-ef8b-4e22-b850-060559f6a2cd">

## Signing up a new user

When you try to sign up as a new user, you might get an email, but the link won't work. 

Or, you'll get this error:

<img width="50%" src="https://github.com/user-attachments/assets/3927a68f-e19b-4938-a1a0-d445fde51a0e">

## Disabling email confirmation 

When signing up a new account, Supabase wants us to confirm our email address. There are two problems with this:
 * Supabase will only try to send 3 email confirmations per hour (so if you just hit the sign up button a few times you're locked out)
 * There's some other funky steps that are required for email confirmations to even work

We will eventually setup email confirmations, but for now we will simply disable email confirmations. To do this:

1. Go to your Supabase dashboard, then go to Authentication in the left sidebar, then go to the Providers section
2. Open the Email provider menu
3. Disable the "Confirm Email" toggle
4. Click Save

<img alt="Screen Shot 2024-07-18 at 2 04 54 PM" src="https://github.com/user-attachments/assets/f9154f1c-eb79-4d25-b456-11c835f8ad40">

## Actually signing up a new user

Now when you go back to your app and sign up as a new user, you should get taken to the Account page!

It looks like this:

<img width="400" alt="Account Page" src="https://github.com/user-attachments/assets/861c788b-bb84-4237-94f4-c5ca5efde4ab">

<table><tr><td>
<details>
  <summary>Gray Buttons on Signin/Signup?</summary>
  
  <br/>
  
  Common error - When you tap signin/signup, nothing happens except the buttons turning gray like this:
  
  <img width="400" alt="image" src="https://github.com/user-attachments/assets/ca3492ee-80eb-4e72-ae37-7302b1e30a07" />
  
  If you added a bunch of console.logs and looked up the error, you'd find there is actually an [open Github Issue for this problem](https://github.com/supabase/supabase-js/issues/1504), and for now the fix is to add this to your `index.js`, just below the imports

```
if (typeof global.structuredClone === "undefined") { global.structuredClone = (value) => JSON.parse(JSON.stringify(value)); }
```
  
  <br/>

</details>
</td></tr></table>




Now you can edit this user profile and see the changes in the profiles table on Supabase!

*Note there are actually two tables that track data about our users. There's the "profiles" table that we've been looking at, and also the authentication Users table, that's semi-hidden. You can see in the Authentication tab if you go to the MANAGE > Users section. If you ever need to delete a user to test part of the account creation/signup process, remember to delete them from the authentication Users table!*

### Milestone Finished

You're done with this milestone when you can edit the username/website data of a user from your app, and see those changes reflected in the "profiles" table.

<img width="20%" alt="Screen Shot 2024-07-18 at 2 20 11 PM" src="https://github.com/user-attachments/assets/71898e0b-028c-43db-911c-b1d8b7219aa8"> <img width="78%" alt="Screen Shot 2024-07-18 at 2 20 11 PM" src="https://github.com/user-attachments/assets/d61e17b8-8bab-4417-9827-f11e197760c4">

## Bonus: Profile Pictures

When you finish the milestone, try continuing the steps in the documentation to get Profile Pictures working!

You'll have to fix a lot more weird TypeScript bits, but you can figure it out!

https://supabase.com/docs/guides/getting-started/tutorials/with-expo-react-native#bonus-profile-photos

<br>

<br>
