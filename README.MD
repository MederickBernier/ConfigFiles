
# **Project Standards Setup**

This repository is a template designed to help you enforce consistent coding standards and best practices across your projects. By following this guide, you'll learn how to set up and use tools like **EditorConfig**, **ESLint**, **Stylelint**, and **Prettier** to ensure clean, maintainable, and professional-grade code.

## **Table of Contents**
1. [Purpose](#purpose)
2. [Features](#features)
3. [Prerequisites](#prerequisites)
4. [Setup Instructions](#setup-instructions)
    - [1. Install VSCode Extensions](#1-install-vscode-extensions)
    - [2. Install Dependencies](#2-install-dependencies)
    - [3. Add VSCode Settings](#3-add-vscode-settings)
    - [4. Start Coding](#4-start-coding)
5. [File Descriptions](#file-descriptions)
6. [How to Use the Linting Tools](#how-to-use-the-linting-tools)
7. [Why Standards Matter](#why-standards-matter)
8. [Troubleshooting](#troubleshooting)
9. [Resources](#resources)

---

## **Purpose**

This setup ensures:
- Consistent code formatting and style across all files and team members.
- Enforced naming conventions for better readability and maintainability.
- Automated linting and formatting to save time and avoid manual corrections.

---

## **Features**

- **EditorConfig**: Enforces consistent file formatting (e.g., indentation, line endings).
- **ESLint**: Lints and enforces naming conventions for JavaScript, TypeScript, and JSX/TSX files.
- **Stylelint**: Lints CSS/SCSS files for consistency and naming conventions.
- **Prettier**: Automatically formats code to match the defined style.
- **VSCode Integration**: Auto-lints and formats files on save.

---

## **Prerequisites**

Before you begin, ensure you have the following:
1. **Node.js** (v16 or later): [Download Node.js](https://nodejs.org/).
2. **VSCode**: [Download VSCode](https://code.visualstudio.com/).

---

## **Setup Instructions**

### **1. Install VSCode Extensions**
Install the following extensions from the VSCode Marketplace:
- [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [Stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
- [Prettier - Code Formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) (optional but recommended)

---

### **2. Install Dependencies**
Download all the configs files and run the following single command to install all required development dependencies:

```bash
npm install eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-react stylelint stylelint-config-standard prettier eslint-config-prettier eslint-plugin-prettier --save-dev
```

---

### **3. Add VSCode Settings**
The `.vscode/settings.json` file contains essential configurations for linting and formatting. Follow these steps to apply it:

1. Open your project in VSCode.
2. Navigate to the **Explorer** view (Ctrl+Shift+E).
3. Locate or create a folder named `.vscode` in the root of your project.
4. Inside the `.vscode` folder, create a file named `settings.json`.
5. Copy and paste the following content into `settings.json`:

   ```json
   {
     "editor.formatOnSave": true,
     "editor.codeActionsOnSave": {
      "source.fixAll": "always"
     },
     "eslint.validate": ["javascript", "javascriptreact", "typescript", "typescriptreact"],
     "stylelint.validate": ["css", "scss"],
     "files.eol": "\n",
   }
   ```

6. Save the file. Your editor is now configured to auto-format and lint your files on save.

---

### **4. Start Coding**
You’re ready to start coding! All tools will now automatically lint and format your code according to the standards when you save files.

---

## **File Descriptions**

### **`.editorconfig`**
Defines formatting rules for all file types, including:
- Indentation style (spaces) and size (2 spaces).
- Line endings (LF).
- Trims trailing whitespace.
- Ensures a newline at the end of files.

### **`.eslintrc.json`**
Defines linting rules and naming conventions for JavaScript, TypeScript, and JSX/TSX:
- Enforces camelCase for variables and functions.
- Enforces PascalCase for React components, interfaces, and types.
- Detects and fixes common errors.

### **`.stylelintrc.json`**
Defines linting rules for CSS/SCSS:
- Enforces BEM methodology for class names.
- Enforces kebab-case for IDs.
- Ensures consistent indentation and quotes.

### **`.prettierrc`**
(Optional) Configures Prettier to auto-format code:
- Single quotes for strings.
- Semicolons at the end of statements.
- Trailing commas in multiline structures.

### **`.vscode/settings.json`**
Configures VSCode to:
- Auto-format and lint files on save.
- Validate JavaScript/TypeScript with ESLint.
- Validate CSS/SCSS with Stylelint.

---

## **How to Use the Linting Tools**

### **1. Manually Check and Fix Linting Issues**
- **JavaScript/TypeScript:**
  ```bash
  npx eslint . --fix
  ```
- **CSS/SCSS:**
  ```bash
  npx stylelint "**/*.css" --fix
  ```

### **2. Auto-Formatting**
- Save your file in VSCode, and it will automatically fix formatting issues.

---

## **Why Standards Matter**

### **1. Consistency**
Shared standards ensure that all code in the project looks and behaves the same, regardless of who wrote it.

### **2. Readability**
Clean and consistent code is easier to understand, debug, and maintain.

### **3. Collaboration**
Standards help teams work together more efficiently, avoiding merge conflicts and style debates.

### **4. Professionalism**
Employers expect developers to follow coding standards and use tools like ESLint, Stylelint, and Prettier in professional projects.

---

## **Troubleshooting**

### **1. Linting Errors Are Not Being Fixed**
- Ensure you’ve installed the required extensions and dependencies.
- Check that the configuration files are correctly placed in the project root.

### **2. Auto-Formatting Not Working in VSCode**
- Verify that `editor.formatOnSave` is enabled in your VSCode settings.
- Restart VSCode after installing extensions or making changes.

### **3. ESLint/Stylelint Errors in Terminal**
- Run the linting command manually to debug the issue:
  ```bash
  npx eslint . --fix
  npx stylelint "**/*.css" --fix
  ```

---

## **Resources**

- [EditorConfig Documentation](https://editorconfig.org/)
- [ESLint Documentation](https://eslint.org/)
- [Stylelint Documentation](https://stylelint.io/)
- [Prettier Documentation](https://prettier.io/)

---

## **Next Steps**

Feel free to extend this setup to include additional tools or configurations as needed for your projects. Happy coding!


---

## **Add Useful Scripts to `package.json`**

You can define scripts in your `package.json` file to make running linting and formatting tasks more convenient. Add the following scripts to the `scripts` section of your `package.json`:

```json
"scripts": {
  "lint:js": "eslint . --ext .js,.jsx,.ts,.tsx",
  "lint:css": "stylelint \"**/*.css\" \"**/*.scss\"",
  "lint:fix": "npm run lint:js -- --fix && npm run lint:css -- --fix",
  "format": "prettier --write ."
}
```

### **Explanation of Scripts**
1. **`lint:js`:** Runs ESLint on all JavaScript, TypeScript, and JSX/TSX files.
2. **`lint:css`:** Runs Stylelint on all CSS and SCSS files.
3. **`lint:fix`:** Runs both JavaScript/TypeScript and CSS/SCSS linting with auto-fixing enabled.
4. **`format`:** Runs Prettier to format all files in the project.

---

### **How to Use These Scripts**
After adding these scripts to `package.json`, you can run them using `npm run`:

1. **Run ESLint:**
   ```bash
   npm run lint:js
   ```

2. **Run Stylelint:**
   ```bash
   npm run lint:css
   ```

3. **Fix Linting Issues:**
   ```bash
   npm run lint:fix
   ```

4. **Format Code with Prettier:**
   ```bash
   npm run format
   ```

---

By adding these scripts to your project, you can streamline your workflow and ensure consistent code quality across your project.
