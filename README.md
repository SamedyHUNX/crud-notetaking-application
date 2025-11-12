# 📝 CRUD Note-Taking Application

A fully functional note-taking application built with **pure HTML, CSS, and JavaScript** - no frameworks, no libraries, just vanilla web technologies! This project represents my early coding learning experience, demonstrating core web development fundamentals.

## ✨ Features

- **Full CRUD Operations**: Create, Read, Update, and Delete notes seamlessly
- **Multi-Language Support**: Switch between English, German, Cambodian, and Thai languages
- **Local Storage**: All notes are automatically saved to browser's local storage
- **Responsive Design**: Works beautifully on desktop and mobile devices
- **Clean UI**: Modern and intuitive user interface
- **Real-time Updates**: Instant note rendering and updates
- **Keyboard Support**: Press Enter to quickly add notes

## 🛠️ Tech Stack

This project is built using **only**:

- **HTML5** - Semantic markup and structure
- **CSS3** - Custom styling and responsive design
- **Vanilla JavaScript** - No frameworks or libraries, pure ES6+ JavaScript

No build tools, no package managers, no dependencies - just pure web technologies!

## 📁 Project Structure

```
crud-notetaking-application/
├── assets/
│   ├── font/          # Custom SF Pro fonts
│   ├── images/        # Image assets
│   └── svg/           # SVG icons and flags
├── components/        # Reusable component modules
│   ├── aside/         # Sidebar navigation
│   ├── button/        # Button components
│   ├── crud/          # CRUD operations logic
│   ├── footer/        # Footer component
│   ├── homepage/      # Homepage intro section
│   ├── input/         # Input field components
│   ├── languages/     # Multi-language translations
│   ├── navbar/        # Navigation bar
│   └── right-section/ # Main content section
├── css/               # Stylesheets
│   ├── common_css/    # Shared styles
│   ├── index.css      # Homepage styles
│   └── note.css       # Note page styles
├── javascript/        # Main JavaScript files
│   ├── index.js       # Homepage logic
│   ├── note.js        # Note page logic
│   └── removal.js     # Element removal utilities
├── index.html         # Homepage
└── note.html          # Main note-taking page
```

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)
- A local web server (optional, but recommended)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/crud-notetaking-application.git
cd crud-notetaking-application
```

2. Open the project:
   - **Option 1**: Simply open `index.html` in your browser
   - **Option 2**: Use a local server for better experience:
     ```bash
     # Using Python
     python -m http.server 8000
     
     # Using Node.js (http-server)
     npx http-server
     
     # Using PHP
     php -S localhost:8000
     ```

3. Navigate to `http://localhost:8000` (if using a server) or open `index.html` directly

## 📖 How to Use

1. **Homepage**: Start at `index.html` to see the welcome screen
2. **Create Notes**: Click "Click to Proceed 👉" to enter the note-taking application
3. **Add a Note**: 
   - Enter a title
   - Add a date (YYYY/MM/DD format)
   - Write your note content
   - Click "Enter Note" or press Enter
4. **Edit Notes**: Click the "Edit" button on any note to modify it
5. **Delete Notes**: Click the "Delete" button to remove a note
6. **Change Language**: Click on any flag icon in the navbar to switch languages
7. **View Notes**: All your notes appear in the sidebar (toggle with the hamburger menu on mobile)

## 🎯 Learning Highlights

This project demonstrates:

- **DOM Manipulation**: Creating, updating, and removing elements dynamically
- **Event Handling**: Click events, keyboard events, and media query listeners
- **Local Storage API**: Persisting data in the browser
- **Component Architecture**: Organizing code into reusable modules
- **Responsive Design**: Media queries and mobile-first approach
- **Internationalization**: Multi-language support implementation
- **CSS Architecture**: Organized stylesheets and component-based styling
- **Vanilla JavaScript Best Practices**: ES6+ features, strict mode, and clean code

## 🌐 Supported Languages

- 🇺🇸 English
- 🇩🇪 German (Deutsch)
- 🇰🇭 Cambodian (Khmer)
- 🇹🇭 Thai

## 💾 Data Storage

All notes are stored in the browser's **localStorage**, which means:
- Notes persist across browser sessions
- Data is stored locally on your device
- No server or database required

## 📱 Responsive Design

The application is fully responsive and adapts to different screen sizes:
- Desktop: Full sidebar and main content view
- Mobile/Tablet: Collapsible sidebar with toggle functionality

## 🎨 Customization

Feel free to customize:
- Colors and styling in the CSS files
- Fonts in `assets/font/`
- Translations in `components/languages/languages.js`
- Component behavior in respective JavaScript files

## 📝 Notes

This was created as a learning project to understand:
- Core web development fundamentals
- CRUD operations in frontend applications
- State management with localStorage
- Component-based architecture patterns
- Responsive web design principles

## 🤝 Contributing

This is a personal learning project, but suggestions and feedback are welcome!

## 📄 License

This project is open source and available for educational purposes.

## 👨‍💻 Author

**Vadhna Samedy Hun**

Built with ❤️ using pure HTML, CSS, and JavaScript

---

⭐ If you find this project helpful or interesting, feel free to star it!

