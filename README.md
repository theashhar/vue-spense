# vue-spense
## Expense Tracker Application

## Project Overview
This is a simple and efficient **Expense Tracker Application** built from scratch using **Vue.js 3** and the Composition API with the latest syntax from version 3.2. The project aims to help users manage their finances by tracking income and expenses, providing a clear and structured breakdown of financial transactions.

## Features
- **Total Balance Display:** Shows the current total balance of all transactions.
- **Income and Expense Breakdown:** Separately displays balances for income and expenses.
- **Transaction History:** A visually distinguished list of transactions:
  - Income transactions have a green border.
  - Expense transactions have a red border.
- **Add New Transactions:** Users can add transactions via a form with input validation.
- **Delete Transactions:** Transactions can be removed from the list.
- **Toast Notifications:** Provides user feedback for successful actions and validation errors.
- **Local Storage Integration:** Ensures data persistence across page reloads.

## Tech Stack
- **Vue.js 3.2:** Core framework for building the application.
- **Composition API:** For better component organization and reusability.
- **Toast Notifications:** To enhance user interaction.
- **Local Storage:** For persisting transaction data.

## Installation

### Prerequisites
- Node.js and npm installed on your system.

### Steps to Set Up the Application
1. Clone the repository:
    ```bash
    git clone <repository-url>
    cd expense-tracker-vue
    ```
2. Install dependencies:
    ```bash
    npm install
    ```
3. Run the development server:
    ```bash
    npm run serve
    ```
4. Open your browser and navigate to `http://localhost:8080`.

## Project Structure
```
.
├── src
│   ├── assets
│   ├── components
│   │   ├── Header.vue
│   │   ├── Balance.vue
│   │   ├── IncomeExpenses.vue
│   │   ├── TransactionList.vue
│   │   └── AddTransaction.vue
│   ├── App.vue
│   └── main.js
├── package.json
└── public
```

## Component Breakdown
### 1. **Header Component**
- Displays the application title.

### 2. **Balance Component**
- Dynamically displays the total balance using Vue's reactive features.

### 3. **IncomeExpenses Component**
- Shows separate totals for income and expenses using computed properties.

### 4. **TransactionList Component**
- Renders a list of transactions.
- Conditionally applies styles based on whether the transaction is an income or expense.

### 5. **AddTransaction Component**
- Contains a form to add new transactions.
- Handles input validation and provides toast notifications.

## Key Features and Implementations
### **1. Transaction Deletion**
- Users can remove specific transactions by clicking the delete button.
- Emits custom events to handle deletion logic.
- Updates local storage upon deletion.

### **2. Local Storage Integration**
- Retrieves transaction data from local storage upon component mounting.
- Saves updated transaction data to local storage whenever a transaction is added or deleted.

### **3. Toast Notifications**
- Provides immediate feedback to users on successful operations or errors.

## Future Enhancements
- Edit functionality for transactions.
- Enhanced user interface and animations.
- Advanced filtering and sorting options.

## Conclusion
This Expense Tracker application demonstrates effective state management, reactivity, and component-based architecture using Vue.js 3 and the Composition API. It showcases how modern web development practices can create dynamic and user-friendly applications.

## License
This project is licensed under the MIT License.

---
Thank you for checking out this project! Feel free to contribute or expand on the existing features.

