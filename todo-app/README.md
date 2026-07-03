# Todo List Application

A simple, efficient todo list application with local storage functionality. Built with vanilla JavaScript, HTML, and CSS for a lightweight, fast experience.

## Features

- ✅ Add, edit, and delete todos
- ✅ Mark todos as complete/incomplete
- ✅ Local storage persistence
- ✅ Filter todos (All, Active, Completed)
- ✅ Clear completed todos
- ✅ Todo counter
- ✅ Responsive design
- ✅ Keyboard shortcuts (Enter to add, Delete to remove)

## Tech Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript (ES6+)
- **Storage**: Browser LocalStorage API
- **Build**: Simple, no dependencies required

## Quick Start

### Option 1: Direct Access
1. Open `index.html` in your browser
2. Start adding todos!

### Option 2: Live Server (Recommended)
```bash
# Using Python
python -m http.server 8000

# Using Node.js with http-server
npm install -g http-server
http-server

# Using VS Code Live Server extension
# Right-click index.html → Open with Live Server
```

Access at: `http://localhost:8000`

## Usage

### Adding a Todo
1. Type text in the input field
2. Press `Enter` or click the "Add" button
3. Todo appears in the list

### Completing a Todo
- Click the checkbox next to the todo
- Todo text will be strikethrough when complete

### Editing a Todo
- Double-click on any todo text to edit
- Press `Enter` to save or `Esc` to cancel

### Deleting a Todo
- Click the delete button (🗑️) on the right
- Or select todo and press `Delete` key

### Filtering Todos
- Click **All** to see all todos
- Click **Active** to see incomplete todos only
- Click **Completed** to see completed todos only

### Clear All Completed
- Click "Clear Completed" to remove all done todos

## File Structure

```
todo-app/
├── index.html           # Main HTML structure
├── css/
│   └── style.css        # Styling and layout
├── js/
│   └── app.js           # Application logic
├── README.md            # Documentation
└── .gitignore           # Git configuration
```

## LocalStorage API

The app uses the browser's LocalStorage API to persist todos:

```javascript
// Saved as JSON in localStorage
localStorage.setItem('todos', JSON.stringify(todosArray));
localStorage.getItem('todos');
```

Data is automatically saved after every action and loaded when the page opens.

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Enter` | Add new todo |
| `Escape` | Cancel editing |
| `Delete` | Delete selected todo |
| `Ctrl/Cmd + A` | Select all in input |

## Browser Support

Works on all modern browsers with LocalStorage support:
- Chrome/Edge 4+
- Firefox 3.5+
- Safari 4+
- iOS Safari 3.2+
- Android 2.1+

## API Reference

### Methods

```javascript
// Initialize app
initApp();

// Add a new todo
addTodo(text);

// Delete a todo
deleteTodo(id);

// Toggle todo completion
toggleTodo(id);

// Edit a todo
editTodo(id, newText);

// Get all todos
getAllTodos();

// Get completed todos count
getCompletedCount();

// Save to LocalStorage
saveTodos();

// Load from LocalStorage
loadTodos();
```

## Data Structure

```javascript
{
  id: "1688476800000",
  text: "Buy groceries",
  completed: false,
  created: "2024-07-03T10:00:00Z",
  updated: "2024-07-03T10:00:00Z"
}
```

## Customization

### Change Theme Colors
Edit `css/style.css`:
```css
:root {
  --primary: #3b82f6;
  --success: #10b981;
  --danger: #ef4444;
}
```

### Change Storage Key
Edit `js/app.js`:
```javascript
const STORAGE_KEY = 'my-todos'; // Change this
```

### Add Due Dates
Extend the data structure to include:
```javascript
{
  id: "...",
  text: "...",
  completed: false,
  dueDate: "2024-07-10",
  priority: "high"
}
```

## Performance

- **Size**: ~5KB minified
- **Load Time**: <100ms
- **Storage**: ~1KB per 10 todos
- **Browser Memory**: Minimal footprint

## Security Considerations

- ⚠️ LocalStorage is NOT encrypted
- ⚠️ XSS-vulnerable if todos contain user scripts
- **Solution**: All user input is sanitized via `textContent`

## Troubleshooting

### Todos Not Saving?
- Check if LocalStorage is enabled
- Verify browser storage quota (usually 5-10MB)
- Check browser console for errors

### Todos Disappeared?
- Try clearing browser cache (should not affect localStorage)
- Check if running in private/incognito mode (usually doesn't persist)
- Export data regularly

### Performance Issues?
- Limit todos to <1000 items
- Consider archiving old todos
- Use IndexedDB for larger datasets

## Future Enhancements

- 📅 Due dates and reminders
- 🏷️ Categories/tags
- ⭐ Priority levels
- 🔄 Recurring todos
- 📊 Statistics dashboard
- 🌙 Dark mode
- 🎨 Themes
- ☁️ Cloud sync
- 📱 Mobile app
- 🔔 Notifications

## Export/Import

### Export Todos as JSON
```javascript
const todos = JSON.parse(localStorage.getItem('todos'));
const dataStr = JSON.stringify(todos, null, 2);
const blob = new Blob([dataStr], { type: 'application/json' });
const url = URL.createObjectURL(blob);
const link = document.createElement('a');
link.href = url;
link.download = 'todos-backup.json';
link.click();
```

### Import Todos from JSON
```javascript
// Paste JSON data into browser console
localStorage.setItem('todos', JSON.stringify(importedData));
location.reload();
```

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/new-feature`
3. Make changes and commit
4. Push and create a Pull Request

## License

MIT License - Feel free to use and modify

## Support

- 📧 Report issues on GitHub
- 💬 Suggest features
- 🐛 Help debug problems

---

**Simple. Fast. Reliable. ✓**

Start managing your todos today!
