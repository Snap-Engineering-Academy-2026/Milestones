# 📦 Using Environment Variables in Expo + React Native

This project uses `react-native-dotenv` to securely load environment variables (e.g., API keys) from a `.env` file.

## 🔐 Why This Matters

Hardcoding API keys in your source code is insecure. Environment variables allow you to safely access sensitive information without exposing it in your app logic.

---

## ⚙️ Setup Instructions

### 1. Install Dependencies

```bash
npx expo install react-native-dotenv
npm install --save-dev react-native-dotenv
```

## 2. Create an .env.local file
```
CHATGPT_KEY=sk-XXXXXXXXXXXXXXXXXXXXXXXX
```

## 3 update the babel config
Make sure babel.config.js includes the plugin and lists react-native-reanimated/plugin last:
```
module.exports = function (api) {
  api.cache(true);
  return {
    presets: ["babel-preset-expo"],
    plugins: [
      [
        "module:react-native-dotenv",
        {
          moduleName: "@env",
          path: ".env",
          blacklist: null,
          whitelist: null,
          safe: false,
          allowUndefined: true,
        },
      ],
      "react-native-reanimated/plugin", // ⚠️ This must always be listed last
    ],
  };
};
```
## 4. Use Variables in Code
Import and use your environment variables like this:
```
import { CHATGPT_KEY } from '@env';

console.log("Your ChatGPT API key:", CHATGPT_KEY);
```

Use this example to update your `getChatGPT.js` file located in the utils folder. NOTE this is not a 1:1 transfer you will need to add the key in the correct spot.
```
import { CHATGPT_KEY } from "@env";
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Accept", "application/json");
myHeaders.append("Authorization", `Bearer ${CHATGPT_KEY}`);
export const getChat = async (messages) => {
  const raw = JSON.stringify({
    model: "gpt-4.1-nano",
    messages: messages,
    temperature: 1,
    top_p: 1,
    n: 1,
    stream: false,
    max_tokens: 250,
    presence_penalty: 0,
    frequency_penalty: 0,
  });

  const requestOptions = {
    method: "POST",
    headers: myHeaders,
    body: raw,
    redirect: "follow",
  };

  const response = await fetch(
    "https://api.openai.com/v1/chat/completions",
    requestOptions
  );

  return await response.json();
};
```

## 5. Restart Expo
After making changes to .env or babel.config.js, restart your dev server:

**Ensure your .env file is not tracked in version control by adding this line to your .gitignore**

| Step                     | Why It's Needed                        |
| ------------------------ | -------------------------------------- |
| `.env` file              | Stores secrets outside your code       |
| `babel.config.js` plugin | Tells Babel how to use those variables |
| `react-native-dotenv`    | Provides that plugin functionality     |
| `--save-dev`             | Keeps it out of your production bundle |
