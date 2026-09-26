## 1. Project Title:  Weather-Data-Analyzer-and-Statistics-System
Weather Data Analyzer is a Python project that stores and analyzes daily weather records using lists, tuples, arrays, functions, loops, sorting, and searching. It calculates temperature, humidity, and rainfall statistics, classifies weather data, and provides useful summaries through a modular system.

## 2. Project Overview
This is a console-based (menu-driven) Python application that manages
and analyzes weather observations such as Date, Temperature, Humidity
and Rainfall. It allows a user to add, search, update and delete
weather records, and to run temperature/rainfall analysis,
classification, statistics, and generate a summary report.

## 3. Problem Being Solved
Manually going through a list of daily weather observations to find
the hottest day, the total rainfall, or how many days were "hot" is
slow and error-prone when done by hand. This project automates that
analysis using simple Python lists, tuples, loops, and conditional
statements.

## 4. Objectives
- Store weather records using a list of tuples.
- Allow the user to manage (add/search/update/delete) weather records.
- Analyze temperature and rainfall data.
- Classify weather conditions using project-defined rules.
- Generate overall statistics and a summary report.
- Practice fundamental Python concepts: lists, tuples, loops,
  conditionals, functions, and basic array algorithms.

## 5. Features
1. Add Weather Record
2. Display All Records
3. Search Weather Record
4. Update Weather Record
5. Delete Weather Record
6. Temperature Analysis (average, max, min, hottest/coldest day, sort,
   counting hot/moderate/cold days)
7. Rainfall Analysis (total, average, max, min, highest rainfall day,
   rainy/dry day counts, sorting)
8. Weather Classification (temperature and rainfall categories)
9. Sort Weather Records (by temperature or rainfall)
10. Find Hottest and Coldest Days
11. Find Kth Hottest/Coldest Day
12. Weather Statistics
13. Generate Summary Report
14. Array Concepts Demo (traversal, max/min, sort, reverse, counting,
    duplicate removal, partitioning, Kth smallest element)

## 6. Technologies Used
- Python 3 (standard library only, no external packages required)

## 7. Python Concepts Used
- Lists and list operations (append, insert, remove, pop, indexing,
  slicing, traversal, sort, reverse)
- Tuples and tuple operations (creation, indexing, slicing, tuple
  unpacking, immutability)
- Array concepts (traversal, maximum/minimum, counting, duplicate
  removal, partitioning, Kth smallest/largest element)
- Conditional statements: if, if-else, if-elif-else, nested if
- Loops: for loop, while loop, break, continue
- Functions (with docstrings) and modular file organization
- Basic error handling using try/except (ValueError)

## 8. Project Structure
```
WeatherDataAnalyzer/
│
├── main.py
├── weather_data.py
├── weather_operations.py
├── temperature_analysis.py
├── rainfall_analysis.py
├── weather_classification.py
├── statistics_analysis.py
├── validation.py
│
├── README.md
├── statement.md
└── requirements.txt
```

## 9. How to Run (Windows)
1. Install Python 3 from https://www.python.org/downloads/ if not
   already installed. During installation, check "Add Python to PATH".
2. Extract/copy the `WeatherDataAnalyzer` folder to your computer.
3. Open Command Prompt.
4. Navigate to the project folder:
   ```
   cd path\to\WeatherDataAnalyzer
   ```
5. Run the program:
   ```
   python main.py
   ```

## 10. How to Use
- After running `main.py`, the main menu is displayed.
- Enter the number corresponding to the operation you want to perform.
- Follow the on-screen prompts (e.g., enter date, temperature, etc.).
- Choose option 15 to exit the program.

## 11. Sample Output
```
==================================================
           WEATHER DATA ANALYZER
==================================================
1. Add Weather Record
2. Display All Records
...
15. Exit
==================================================
Enter your choice: 12

--- Weather Statistics ---
Number of Records: 15
Average Temperature: 28.87 C
Maximum Temperature: 36 C
Minimum Temperature: 18 C
...
```

## 12. Testing
See the Testing section in the Project Report (`Project_Report.md`)
for a table of at least 15 test cases covering valid input, invalid
input, and edge cases (empty dataset, nonexistent date, invalid K,
etc.). All test cases were manually run against `main.py` and produced
the expected output without the program crashing.

## 13. Future Enhancements
The following are NOT implemented in the current basic project. They
are listed only as possible future improvements:
- Live weather API integration
- Graphical user interface (GUI)
- Database storage (SQLite/MySQL) instead of in-memory list
- Data visualization (charts/graphs of temperature and rainfall trends)
- CSV import/export of weather records
