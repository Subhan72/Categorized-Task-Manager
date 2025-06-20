# Categorized Task Manager

A comprehensive task management application built with React that enables users to organize, prioritize, and track their tasks with advanced filtering and sorting capabilities.

## 🚀 Features

### Core Functionality
- **Task Creation**: Add tasks with title, category, priority, and deadline
- **Task Management**: Mark tasks as complete/incomplete and delete unwanted tasks
- **Smart Organization**: Categorize tasks for better workflow management
- **Priority System**: Assign and sort tasks by priority levels
- **Deadline Tracking**: Set and monitor task deadlines

### Advanced Features
- **Multi-Filter System**: Filter tasks by category, priority, and completion status
- **Dynamic Sorting**: Sort tasks by deadline, priority, or creation date
- **Real-time Search**: Search tasks by title with instant results
- **Category Analytics**: View task count statistics by category
- **Responsive Design**: Optimized for all device sizes

### User Experience
- **Intuitive Interface**: Clean, modern design with smooth interactions
- **Visual Indicators**: Color-coded priorities and status badges
- **Quick Actions**: One-click task completion and deletion
- **Persistent Data**: Tasks saved to local storage for session continuity

## 🛠️ Technical Implementation

### Task Data Structure

```javascript
const taskSchema = {
  id: "unique-identifier",
  title: "Task title",
  category: "work|personal|health|education|other",
  priority: "high|medium|low",
  deadline: "YYYY-MM-DD",
  completed: false,
  createdAt: "timestamp",
  completedAt: "timestamp|null"
};
```

### Component Architecture

**TaskForm Component**
- Controlled form inputs with validation
- Category and priority selection
- Date picker for deadline setting
- Form submission handling with validation

**TaskList Component**
- Renders filtered and sorted task collection
- Handles task completion toggle
- Manages task deletion with confirmation
- Empty state handling

**TaskItem Component**
- Individual task display with all properties
- Interactive completion checkbox
- Priority and deadline visual indicators
- Edit and delete action buttons

**FilterBar Component**
- Category filter dropdown
- Priority filter options
- Search input with debounced queries
- Sort options (deadline, priority, created date)
- Clear filters functionality

### State Management

```javascript
const [tasks, setTasks] = useState([]);
const [filters, setFilters] = useState({
  category: 'all',
  priority: 'all',
  status: 'all',
  search: ''
});
const [sortBy, setSortBy] = useState('deadline');
```

## 🎨 Design Features

### Priority Color Coding
- **High Priority**: Red indicators and badges
- **Medium Priority**: Yellow/Orange indicators
- **Low Priority**: Green indicators
- **Completed Tasks**: Muted/strikethrough styling

### Category System
- **Work**: Professional and business tasks
- **Personal**: Individual and family tasks
- **Health**: Fitness and wellness activities
- **Education**: Learning and development goals
- **Other**: Miscellaneous tasks

### Visual Elements
- Task completion animations
- Priority badges and icons
- Deadline proximity warnings
- Category color themes
- Status change transitions

## 📊 Filtering & Sorting

### Filter Options
- **By Category**: Filter tasks by specific categories
- **By Priority**: Show only high, medium, or low priority tasks
- **By Status**: View completed, incomplete, or all tasks
- **By Search**: Real-time title-based search functionality

### Sorting Capabilities
- **By Deadline**: Ascending/descending date order
- **By Priority**: High to low or low to high
- **By Creation Date**: Newest or oldest first
- **By Completion Status**: Completed vs incomplete

### Advanced Filtering
```javascript
const filteredTasks = tasks.filter(task => {
  const matchesCategory = filters.category === 'all' || task.category === filters.category;
  const matchesPriority = filters.priority === 'all' || task.priority === filters.priority;
  const matchesStatus = filters.status === 'all' || 
    (filters.status === 'completed' && task.completed) ||
    (filters.status === 'incomplete' && !task.completed);
  const matchesSearch = task.title.toLowerCase().includes(filters.search.toLowerCase());
  
  return matchesCategory && matchesPriority && matchesStatus && matchesSearch;
});
```

## 📱 Responsive Design

### Breakpoint Strategy
- **Mobile (320px+)**: Stacked layout with touch-friendly interactions
- **Tablet (768px+)**: Two-column layout with expanded filters
- **Desktop (1024px+)**: Full-width layout with sidebar navigation

### Mobile Optimizations
- Touch-friendly buttons and checkboxes
- Swipe gestures for task actions
- Collapsible filter panel
- Optimized form inputs for mobile keyboards

## 💾 Data Persistence

### Local Storage Integration
- Automatic task saving on every change
- Data restoration on app reload
- Backup and restore functionality
- Session management

### Data Management
```javascript
// Save tasks to localStorage
const saveTasks = (tasks) => {
  localStorage.setItem('taskManager_tasks', JSON.stringify(tasks));
};

// Load tasks from localStorage
const loadTasks = () => {
  const saved = localStorage.getItem('taskManager_tasks');
  return saved ? JSON.parse(saved) : [];
};
```

## 🔍 Search Functionality

### Real-time Search
- Instant search results as user types
- Case-insensitive matching
- Highlights matching text in results
- Search across task titles and descriptions

### Search Features
- **Debounced Input**: Optimized performance with delayed search execution
- **Clear Search**: One-click search reset
- **Search Suggestions**: Recently searched terms
- **No Results State**: Helpful message when no tasks match

## 📈 Analytics & Statistics

### Category Statistics
- Task count per category
- Completion rate by category
- Priority distribution
- Deadline proximity analysis

### Dashboard Metrics
- Total tasks created
- Completion percentage
- Overdue task count
- Today's tasks summary

## ⚡ Performance Optimizations

### React Optimizations
- **useMemo**: Memoized filtered and sorted task lists
- **useCallback**: Optimized event handlers
- **Lazy Loading**: Conditional component rendering
- **Virtual Scrolling**: For large task lists

### State Management
- Efficient state updates with functional updates
- Minimal re-renders through proper key usage
- Optimized filtering and sorting algorithms

## 🛡️ Validation & Error Handling

### Form Validation
- Required field validation
- Date validation (no past deadlines)
- Title length restrictions
- Category and priority selection validation

### Error States
- Form submission errors
- Data loading failures
- Invalid date entries
- Network connectivity issues

## 🎯 Key Learning Outcomes

This project demonstrates proficiency in:

- **React Fundamentals**: Props, state, and component lifecycle
- **State Management**: Complex state with multiple filters and sorting
- **Component Design**: Reusable, maintainable component architecture
- **Event Handling**: Form submissions, user interactions, and data updates
- **Data Filtering**: Advanced filtering logic with multiple criteria
- **Sorting Algorithms**: Dynamic sorting with multiple parameters
- **Local Storage**: Data persistence and retrieval
- **Responsive Design**: Mobile-first approach with breakpoint management
- **Performance**: Optimized rendering and state updates

## 🔧 Technologies Used

- **React** (Hooks, State Management, Component Architecture)
- **JavaScript ES6+** (Array methods, destructuring, async/await)
- **CSS3** (Flexbox, Grid, Animations, Media Queries)
- **HTML5** (Semantic markup, Form validation)
- **Local Storage API** (Data persistence)
- **Date API** (Date manipulation and formatting)

## 🎉 Getting Started

1. Clone the repository
2. Install dependencies: `npm install`
3. Start development server: `npm start`
4. Open http://localhost:3000 to view the application

## 📋 Usage Examples

### Adding a Task
1. Click "Add New Task" button
2. Fill in task title, select category and priority
3. Set deadline using date picker
4. Click "Create Task" to save

### Filtering Tasks
1. Use category dropdown to filter by specific categories
2. Select priority level from priority filter
3. Toggle between completed/incomplete tasks
4. Use search bar for title-based filtering

### Managing Tasks
1. Click checkbox to mark tasks as complete
2. Use delete button to remove unwanted tasks
3. Sort tasks using the sort dropdown
4. View category statistics in the sidebar

## 🔮 Future Enhancements

- **Task Subtasks**: Break down complex tasks into smaller items
- **Due Date Notifications**: Browser notifications for approaching deadlines
- **Task Templates**: Reusable task templates for common activities
- **Export/Import**: CSV export and import functionality
- **Collaboration**: Share tasks with team members
- **Advanced Analytics**: Detailed productivity insights and reports
- **Drag & Drop**: Reorder tasks and change priorities with drag and drop
- **Task Notes**: Add detailed descriptions and notes to tasks

## 🏆 Project Highlights

- **Component Reusability**: Modular components that can be easily extended
- **Performance Optimized**: Efficient filtering and sorting with large datasets
- **User-Centric Design**: Intuitive interface focused on productivity
- **Data Integrity**: Robust validation and error handling
- **Scalable Architecture**: Easy to extend with new features

---

*This task manager showcases practical React development skills with real-world application features, demonstrating proficiency in state management, component design, and user experience optimization.*
