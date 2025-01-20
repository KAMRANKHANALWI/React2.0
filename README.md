# Password Generator

## Overview

This project is a simple password generator built with React. Users can customize the password by selecting the length, including numbers, and adding special characters. The project reinforces important React concepts such as state management, side effects, and performance optimization.

## Features

- Adjust password length
- Include numbers and special characters
- Copy password to clipboard
- Responsive design using Tailwind CSS

## Tech Stack

- **Frontend:** React, Vite, Tailwind CSS

## How to Run the Project

1. Clone the repository:
   ```sh
   git clone https://github.com/KAMRANKHANALWI/React2.0.git
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Start the development server:
   ```sh
   npm run dev
   ```
4. Open `http://localhost:5173` in your browser.

## Concepts Learned

1. **State Management with `useState`**

   - `useState` is used to store and update stateful values in a functional component. It helps manage dynamic data such as form inputs, UI toggles, and local component states.
   - Managing password length, inclusion of numbers and special characters, and the generated password.
   - Example:
     ```jsx
     const [length, setLength] = useState(8);
     const [numberAllowed, setNumberAllowed] = useState(false);
     const [charAllowed, setCharAllowed] = useState(false);
     const [password, setPassword] = useState("");
     ```

2. **Side Effects with `useEffect`**

   - `useEffect` allows you to perform side effects in function components, such as fetching data, subscriptions, and manual DOM manipulation.
   - Automatically updating the generated password when dependencies change.
   - Example:
     ```jsx
     useEffect(() => {
       generatePassword();
     }, [length, numberAllowed, charAllowed]);
     ```

3. **Performance Optimization with `useCallback`**

   - `useCallback` memoizes functions to prevent them from being recreated on every render, improving performance.
   - Memoizing functions to prevent unnecessary re-renders.
   - Example:
     ```jsx
     const generatePassword = useCallback(() => {
       let pass = "";
       let str = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
       if (numberAllowed) str += "0123456789";
       if (charAllowed) str += "!@#$%^&*()_+";
       for (let i = 1; i <= length; i++) {
         pass += str.charAt(Math.floor(Math.random() * str.length));
       }
       setPassword(pass);
     }, [length, numberAllowed, charAllowed]);
     ```

4. **Referencing Elements with `useRef`**
   - `useRef` provides a way to access and interact with DOM elements directly without triggering re-renders.
   - Accessing input fields without causing re-renders.
   - Example:
     ```jsx
     const passwordRef = useRef(null);
     ```

## License

This project is licensed under the MIT License.
