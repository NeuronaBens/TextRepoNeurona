// utils/database.js

// Simulated database object
const database = {
  users: [
    { id: 1, name: "John Doe", email: "john@example.com" },
    { id: 2, name: "Jane Smith", email: "jane@example.com" },
    // Add more user data as needed
  ],
  // Add more collections or data as needed
};

// Functions to interact with the simulated database
export const getUsers = () => {
  return database.users;
};

export const getUserById = (id) => {
  return database.users.find((user) => user.id === id);
};

export const addUser = (user) => {
  database.users.push(user);
};

// Add more functions for CRUD operations as needed

export default database;
