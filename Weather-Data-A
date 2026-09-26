"""
Weather Data Analyzer and Statistics System
---------------------------------------------
SINGLE-FILE VERSION

This is a single-file version of the project. It contains the exact
same code as the multi-file version, just combined into one file so
it can be run directly with:

    python weather_analyzer.py

with no folder structure or import path issues.
"""


# ======================================================================
# ---- Content originally from validation.py ----
# ======================================================================
"""
validation.py
--------------
This file contains simple, beginner-friendly functions used to
validate user input across the project. Using functions here avoids
repeating the same try/except and if-else validation code in many
places (Module 8: Validation and Error Handling).
"""


def get_valid_menu_choice(min_choice, max_choice):
    """
    Ask the user for a menu choice and keep asking until a valid
    integer within range is entered. Uses a while loop and try/except.
    """
    while True:
        choice_input = input("Enter your choice: ")
        try:
            choice = int(choice_input)
        except ValueError:
            print("Invalid input. Please enter a number.")
            continue

        if choice < min_choice or choice > max_choice:
            print("Invalid choice. Please choose a number between",
                  min_choice, "and", max_choice)
        else:
            return choice


def get_valid_date():
    """
    Ask the user for a date in DD-MM-YYYY format.
    Basic validation: the date string must have exactly 3 parts
    separated by '-', and each part must be a number.
    """
    while True:
        date_str = input("Enter date (DD-MM-YYYY): ")
        parts = date_str.split("-")

        if len(parts) != 3:
            print("Invalid date format. Please use DD-MM-YYYY.")
            continue

        day_part, month_part, year_part = parts

        if day_part.isdigit() and month_part.isdigit() and year_part.isdigit():
            day = int(day_part)
            month = int(month_part)
            if 1 <= day <= 31 and 1 <= month <= 12:
                return date_str
            else:
                print("Invalid day or month value.")
        else:
            print("Invalid date format. Please use DD-MM-YYYY with numbers only.")


def get_valid_temperature():
    """Ask the user for temperature and validate it is a number."""
    while True:
        temp_input = input("Enter temperature (in Celsius): ")
        try:
            temperature = int(temp_input)
            # A simple realistic range check
            if -50 <= temperature <= 60:
                return temperature
            else:
                print("Temperature out of realistic range (-50 to 60).")
        except ValueError:
            print("Invalid temperature. Please enter a whole number.")


def get_valid_humidity():
    """Ask the user for humidity percentage and validate range 0-100."""
    while True:
        humidity_input = input("Enter humidity (in %): ")
        try:
            humidity = int(humidity_input)
            if 0 <= humidity <= 100:
                return humidity
            else:
                print("Humidity must be between 0 and 100.")
        except ValueError:
            print("Invalid humidity. Please enter a whole number.")


def get_valid_rainfall():
    """Ask the user for rainfall in mm and validate it is not negative."""
    while True:
        rainfall_input = input("Enter rainfall (in mm): ")
        try:
            rainfall = int(rainfall_input)
            if rainfall >= 0:
                return rainfall
            else:
                print("Rainfall cannot be negative.")
        except ValueError:
            print("Invalid rainfall. Please enter a whole number.")


def get_valid_k(max_value):
    """Ask the user for a valid K value (1 to max_value) for Kth element."""
    while True:
        k_input = input("Enter the value of K: ")
        try:
            k = int(k_input)
            if 1 <= k <= max_value:
                return k
            else:
                print("K must be between 1 and", max_value)
        except ValueError:
            print("Invalid input. Please enter a whole number.")


# ======================================================================
# ---- Content originally from weather_data.py ----
# ======================================================================
"""
weather_data.py
----------------
This file stores the initial sample weather data for the Weather Data
Analyzer project.

DATA STRUCTURE DESIGN
----------------------
We use a LIST OF TUPLES to store weather records.

- The OUTER structure is a LIST because:
    * We need to ADD new records (append)
    * We need to REMOVE records (pop/remove)
    * We need to UPDATE records (replace by index)
    * Lists are mutable, so the list can grow and shrink as the user
      adds or deletes weather records.

- Each INDIVIDUAL weather record is a TUPLE because:
    * A single day's weather record (Date, Temperature, Humidity,
      Rainfall) has a FIXED structure that should not change once
      created.
    * Tuples are immutable, which protects a record from being
      accidentally changed field-by-field.
    * Tuples allow tuple unpacking, which makes the code easy to read,
      e.g.  date, temp, humidity, rainfall = record

Each tuple is arranged as:
    (Date, Temperature, Humidity, Rainfall)
"""

# Sample weather records: (Date, Temperature in C, Humidity in %, Rainfall in mm)
weather_records = [
    ("01-09-2026", 32, 65, 5),
    ("02-09-2026", 34, 60, 0),
    ("03-09-2026", 29, 82, 18),
    ("04-09-2026", 27, 88, 25),
    ("05-09-2026", 31, 70, 8),
    ("06-09-2026", 36, 55, 0),
    ("07-09-2026", 22, 90, 32),
    ("08-09-2026", 18, 95, 40),
    ("09-09-2026", 25, 75, 12),
    ("10-09-2026", 30, 68, 3),
    ("11-09-2026", 33, 62, 0),
    ("12-09-2026", 28, 80, 15),
    ("13-09-2026", 19, 92, 28),
    ("14-09-2026", 35, 58, 0),
    ("15-09-2026", 24, 77, 10),
]


# ======================================================================
# ---- Content originally from weather_classification.py ----
# ======================================================================
"""
weather_classification.py
--------------------------
Module 4 - Weather Classification.

NOTE: The temperature and rainfall classification rules used below are
PROJECT-DEFINED RULES created for this student project. They are NOT
official meteorological standards.

Classification rules used in this project:

Temperature:
    Below 20 C        -> Cold
    20 C to 30 C      -> Moderate
    Above 30 C        -> Hot

Rainfall:
    0 mm              -> Dry
    1 mm  to 10 mm    -> Light Rain
    11 mm to 25 mm    -> Moderate Rain
    Above 25 mm       -> Heavy Rain

These functions demonstrate if-elif-else and nested if usage from the
syllabus.
"""


def classify_temperature(temperature):
    """Classify a single temperature value using if-elif-else."""
    if temperature < 20:
        return "Cold"
    elif temperature <= 30:
        return "Moderate"
    else:
        return "Hot"


def classify_rainfall(rainfall):
    """Classify a single rainfall value using if-elif-else."""
    if rainfall == 0:
        return "Dry"
    elif rainfall <= 10:
        return "Light Rain"
    elif rainfall <= 25:
        return "Moderate Rain"
    else:
        return "Heavy Rain"


def weather_classification_menu(weather_records):
    """
    Display the classification of every weather record.
    Uses a for loop for traversal, tuple unpacking, and the
    classification functions above (nested logic: loop + if-elif-else).
    """
    print("\n--- Weather Classification ---")
    print("(Note: These are project-defined classification rules,")
    print(" not official meteorological standards.)\n")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    print("{:<12}{:<10}{:<15}{:<10}{:<15}".format(
        "Date", "Temp(C)", "Temp Class", "Rain(mm)", "Rain Class"))
    print("-" * 62)

    for record in weather_records:
        date, temperature, humidity, rainfall = record

        temp_class = classify_temperature(temperature)
        rain_class = classify_rainfall(rainfall)

        # Nested if example: highlight days that are both Hot and Dry
        if temp_class == "Hot":
            if rain_class == "Dry":
                note = " (Hot & Dry)"
            else:
                note = ""
        else:
            note = ""

        print("{:<12}{:<10}{:<15}{:<10}{:<15}".format(
            date, temperature, temp_class, rainfall, rain_class) + note)


# ======================================================================
# ---- Content originally from weather_operations.py ----
# ======================================================================
"""
weather_operations.py
----------------------
Module 1 - Weather Data Management.

This file contains functions to Add, Display, Search, Update and
Delete weather records. The main data structure is a LIST of TUPLES,
where each tuple represents one weather record:
    (Date, Temperature, Humidity, Rainfall)

List operations used here: append(), pop(), indexing, traversal (for
loop). Tuple concepts used here: tuple creation and tuple unpacking.
"""



def is_date_present(weather_records, date_to_check):
    """
    Check whether a given date already exists in the weather_records
    list. Returns True if found, otherwise False.
    Demonstrates list traversal using a for loop and tuple unpacking.
    """
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        if date == date_to_check:
            return True
    return False


def find_record_index(weather_records, date_to_find):
    """
    Return the index of the record with the given date, or -1 if not
    found. Demonstrates indexing and traversal together.
    """
    for index in range(len(weather_records)):
        date, temperature, humidity, rainfall = weather_records[index]
        if date == date_to_find:
            return index
    return -1


def add_weather_record(weather_records):
    """
    Add a new weather record to the list.
    Uses list.append() to add the new tuple at the end of the list.
    Handles the duplicate date case.
    """
    print("\n--- Add Weather Record ---")
    date = get_valid_date()

    if is_date_present(weather_records, date):
        print("A record for this date already exists. Use Update instead.")
        return

    temperature = get_valid_temperature()
    humidity = get_valid_humidity()
    rainfall = get_valid_rainfall()

    # Creating a tuple for the new record (tuple packing)
    new_record = (date, temperature, humidity, rainfall)
    weather_records.append(new_record)
    print("Weather record added successfully.")


def display_all_records(weather_records):
    """
    Display all weather records using a for loop (list traversal) and
    tuple unpacking to read each field.
    """
    print("\n--- All Weather Records ---")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    print("{:<12}{:<15}{:<12}{:<12}".format("Date", "Temp(C)", "Humidity(%)", "Rainfall(mm)"))
    print("-" * 51)

    for record in weather_records:
        date, temperature, humidity, rainfall = record
        print("{:<12}{:<15}{:<12}{:<12}".format(date, temperature, humidity, rainfall))


def search_weather_record(weather_records):
    """
    Search for a weather record by date.
    Demonstrates linear search using a for loop.
    """
    print("\n--- Search Weather Record ---")

    if len(weather_records) == 0:
        print("No weather records available to search.")
        return

    search_date = input("Enter date to search (DD-MM-YYYY): ")
    found = False

    for record in weather_records:
        date, temperature, humidity, rainfall = record
        if date == search_date:
            found = True
            print("Record found:")
            print("Date:", date)
            print("Temperature:", temperature, "C")
            print("Humidity:", humidity, "%")
            print("Rainfall:", rainfall, "mm")
            break

    if not found:
        print("No record found for date:", search_date)


def update_weather_record(weather_records):
    """
    Update an existing weather record.
    Since tuples are immutable, we cannot change one field of a tuple
    directly. Instead, we build a brand-new tuple with the updated
    values and REPLACE the old tuple in the list using indexing.
    This clearly shows: list is mutable (can replace an item by
    index), tuple is immutable (must be recreated, not modified).
    """
    print("\n--- Update Weather Record ---")

    if len(weather_records) == 0:
        print("No weather records available to update.")
        return

    update_date = input("Enter date of record to update (DD-MM-YYYY): ")
    index = find_record_index(weather_records, update_date)

    if index == -1:
        print("No record found for date:", update_date)
        return

    print("Enter new values for the record:")
    temperature = get_valid_temperature()
    humidity = get_valid_humidity()
    rainfall = get_valid_rainfall()

    # Build a new tuple (tuples cannot be modified in place)
    updated_record = (update_date, temperature, humidity, rainfall)

    # Replace the old tuple in the list using list indexing (list is mutable)
    weather_records[index] = updated_record
    print("Weather record updated successfully.")


def delete_weather_record(weather_records):
    """
    Delete a weather record by date.
    Demonstrates list.pop() using an index found through search.
    """
    print("\n--- Delete Weather Record ---")

    if len(weather_records) == 0:
        print("No weather records available to delete.")
        return

    delete_date = input("Enter date of record to delete (DD-MM-YYYY): ")
    index = find_record_index(weather_records, delete_date)

    if index == -1:
        print("No record found for date:", delete_date)
        return

    removed_record = weather_records.pop(index)
    print("Deleted record:", removed_record)


# ======================================================================
# ---- Content originally from temperature_analysis.py ----
# ======================================================================
"""
temperature_analysis.py
------------------------
Module 2 - Temperature Analysis.

This file uses basic array/list algorithms taught in the syllabus:
traversal, finding maximum/minimum, sorting, and finding the Kth
smallest/largest element - applied to the temperature values inside
our list of tuples.
"""



def get_temperature_list(weather_records):
    """
    Build a plain list of temperatures from the list of tuples.
    This is the 'temperature array' used to demonstrate array
    concepts such as traversal, max, min, sort, reverse, etc.
    """
    temperatures = []
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        temperatures.append(temperature)
    return temperatures


def average_temperature(weather_records):
    """Calculate average temperature using a for loop (summation)."""
    if len(weather_records) == 0:
        return 0

    total = 0
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        total = total + temperature

    average = total / len(weather_records)
    return average


def hottest_day(weather_records):
    """
    Find the hottest day using the manual maximum-finding algorithm
    taught in the syllabus (Array: Finding the Maximum number in a set).
    """
    hottest_record = weather_records[0]
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        hottest_date, hottest_temp, hottest_hum, hottest_rain = hottest_record
        if temperature > hottest_temp:
            hottest_record = record
    return hottest_record


def coldest_day(weather_records):
    """Find the coldest day using the manual minimum-finding algorithm."""
    coldest_record = weather_records[0]
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        coldest_date, coldest_temp, coldest_hum, coldest_rain = coldest_record
        if temperature < coldest_temp:
            coldest_record = record
    return coldest_record


def sort_records_by_temperature(weather_records, descending=False):
    """
    Return a NEW list of records sorted by temperature.
    Uses a simple bubble-sort style algorithm (fundamental algorithm)
    instead of the built-in sort, so the logic is easy to explain in
    a viva. Works on a cloned list so the original is not disturbed.
    """
    # Clone the list first (list slicing), so original list is untouched
    sorted_records = weather_records[:]
    n = len(sorted_records)

    for i in range(n):
        for j in range(0, n - i - 1):
            date1, temp1, hum1, rain1 = sorted_records[j]
            date2, temp2, hum2, rain2 = sorted_records[j + 1]

            if descending:
                should_swap = temp1 < temp2
            else:
                should_swap = temp1 > temp2

            if should_swap:
                sorted_records[j], sorted_records[j + 1] = sorted_records[j + 1], sorted_records[j]

    return sorted_records


def kth_hottest_day(weather_records):
    """
    Find the Kth hottest day.
    Sorts a copy of the records in descending order of temperature and
    picks the element at index K-1 (Kth largest element algorithm).
    """
    if len(weather_records) == 0:
        print("No weather records available.")
        return

    k = get_valid_k(len(weather_records))
    sorted_desc = sort_records_by_temperature(weather_records, descending=True)
    return sorted_desc[k - 1]


def kth_coldest_day(weather_records):
    """
    Find the Kth coldest day.
    Sorts a copy of the records in ascending order of temperature and
    picks the element at index K-1 (Kth smallest element algorithm).
    """
    if len(weather_records) == 0:
        print("No weather records available.")
        return

    k = get_valid_k(len(weather_records))
    sorted_asc = sort_records_by_temperature(weather_records, descending=False)
    return sorted_asc[k - 1]


def count_temperature_categories(weather_records):
    """
    Count how many days are Hot, Moderate, and Cold.
    Uses a for loop and if-elif-else (counting algorithm).
    """
    hot_count = 0
    moderate_count = 0
    cold_count = 0

    for record in weather_records:
        date, temperature, humidity, rainfall = record
        category = classify_temperature(temperature)

        if category == "Hot":
            hot_count += 1
        elif category == "Moderate":
            moderate_count += 1
        else:
            cold_count += 1

    return hot_count, moderate_count, cold_count


def temperature_analysis_menu(weather_records):
    """Console interface for Module 2 - Temperature Analysis."""
    print("\n--- Temperature Analysis ---")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    print("1. Average Temperature")
    print("2. Maximum Temperature")
    print("3. Minimum Temperature")
    print("4. Hottest Day")
    print("5. Coldest Day")
    print("6. Sort Records by Temperature (Ascending)")
    print("7. Sort Records by Temperature (Descending)")
    print("8. Count Hot / Moderate / Cold Days")
    print("9. Back to Main Menu")

    choice = get_valid_menu_choice(1, 9)

    temperatures = get_temperature_list(weather_records)

    if choice == 1:
        print("Average Temperature:", round(average_temperature(weather_records), 2), "C")
    elif choice == 2:
        print("Maximum Temperature:", max(temperatures), "C")
    elif choice == 3:
        print("Minimum Temperature:", min(temperatures), "C")
    elif choice == 4:
        date, temp, hum, rain = hottest_day(weather_records)
        print("Hottest Day:", date, "with", temp, "C")
    elif choice == 5:
        date, temp, hum, rain = coldest_day(weather_records)
        print("Coldest Day:", date, "with", temp, "C")
    elif choice == 6:
        sorted_records = sort_records_by_temperature(weather_records, descending=False)
        for record in sorted_records:
            print(record)
    elif choice == 7:
        sorted_records = sort_records_by_temperature(weather_records, descending=True)
        for record in sorted_records:
            print(record)
    elif choice == 8:
        hot, moderate, cold = count_temperature_categories(weather_records)
        print("Hot Days:", hot)
        print("Moderate Days:", moderate)
        print("Cold Days:", cold)
    elif choice == 9:
        return


# ======================================================================
# ---- Content originally from rainfall_analysis.py ----
# ======================================================================
"""
rainfall_analysis.py
----------------------
Module 3 - Rainfall Analysis.
"""



def get_rainfall_list(weather_records):
    """Build a plain list of rainfall values from the list of tuples."""
    rainfall_values = []
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        rainfall_values.append(rainfall)
    return rainfall_values


def total_rainfall(weather_records):
    """Calculate total rainfall using a for loop (summation algorithm)."""
    total = 0
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        total = total + rainfall
    return total


def average_rainfall(weather_records):
    """Calculate average rainfall."""
    if len(weather_records) == 0:
        return 0
    return total_rainfall(weather_records) / len(weather_records)


def day_with_highest_rainfall(weather_records):
    """Find the day with the highest rainfall using manual max algorithm."""
    highest_record = weather_records[0]
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        h_date, h_temp, h_hum, h_rain = highest_record
        if rainfall > h_rain:
            highest_record = record
    return highest_record


def count_rainy_and_dry_days(weather_records):
    """
    Count rainy days (rainfall > 0) and dry days (rainfall == 0).
    Uses if-else and a for loop (counting algorithm).
    """
    rainy_days = 0
    dry_days = 0

    for record in weather_records:
        date, temperature, humidity, rainfall = record
        if rainfall > 0:
            rainy_days += 1
        else:
            dry_days += 1

    return rainy_days, dry_days


def sort_records_by_rainfall(weather_records, descending=False):
    """
    Return a new list of records sorted by rainfall using a simple
    bubble-sort style algorithm (fundamental algorithm from syllabus).
    """
    sorted_records = weather_records[:]
    n = len(sorted_records)

    for i in range(n):
        for j in range(0, n - i - 1):
            date1, temp1, hum1, rain1 = sorted_records[j]
            date2, temp2, hum2, rain2 = sorted_records[j + 1]

            if descending:
                should_swap = rain1 < rain2
            else:
                should_swap = rain1 > rain2

            if should_swap:
                sorted_records[j], sorted_records[j + 1] = sorted_records[j + 1], sorted_records[j]

    return sorted_records


def rainfall_analysis_menu(weather_records):
    """Console interface for Module 3 - Rainfall Analysis."""
    print("\n--- Rainfall Analysis ---")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    print("1. Total Rainfall")
    print("2. Average Rainfall")
    print("3. Maximum Rainfall")
    print("4. Minimum Rainfall")
    print("5. Day with Highest Rainfall")
    print("6. Number of Rainy and Dry Days")
    print("7. Sort Records by Rainfall (Ascending)")
    print("8. Sort Records by Rainfall (Descending)")
    print("9. Back to Main Menu")

    choice = get_valid_menu_choice(1, 9)
    rainfall_values = get_rainfall_list(weather_records)

    if choice == 1:
        print("Total Rainfall:", total_rainfall(weather_records), "mm")
    elif choice == 2:
        print("Average Rainfall:", round(average_rainfall(weather_records), 2), "mm")
    elif choice == 3:
        print("Maximum Rainfall:", max(rainfall_values), "mm")
    elif choice == 4:
        print("Minimum Rainfall:", min(rainfall_values), "mm")
    elif choice == 5:
        date, temp, hum, rain = day_with_highest_rainfall(weather_records)
        print("Highest Rainfall Day:", date, "with", rain, "mm")
    elif choice == 6:
        rainy, dry = count_rainy_and_dry_days(weather_records)
        print("Rainy Days:", rainy)
        print("Dry Days:", dry)
    elif choice == 7:
        sorted_records = sort_records_by_rainfall(weather_records, descending=False)
        for record in sorted_records:
            print(record)
    elif choice == 8:
        sorted_records = sort_records_by_rainfall(weather_records, descending=True)
        for record in sorted_records:
            print(record)
    elif choice == 9:
        return


# ======================================================================
# ---- Content originally from statistics_analysis.py ----
# ======================================================================
"""
statistics_analysis.py
------------------------
Module 5 - Statistics Analysis.

This file also demonstrates the ARRAY CONCEPTS from the syllabus
(Unit V: traversal, maximum, minimum, sorting, reverse, counting,
duplicate removal, partitioning, Kth smallest element) using the
temperature values as an example array/list.
"""



def get_humidity_list(weather_records):
    """Build a plain list of humidity values from the list of tuples."""
    humidity_values = []
    for record in weather_records:
        date, temperature, humidity, rainfall = record
        humidity_values.append(humidity)
    return humidity_values


def overall_statistics(weather_records):
    """
    Calculate and print overall statistics for the weather dataset.
    Combines earlier module functions (reuse instead of duplicating code).
    """
    print("\n--- Weather Statistics ---")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    temperatures = get_temperature_list(weather_records)
    humidity_values = get_humidity_list(weather_records)

    hot_count = 0
    moderate_count = 0
    cold_count = 0

    for record in weather_records:
        date, temperature, humidity, rainfall = record
        category = classify_temperature(temperature)
        if category == "Hot":
            hot_count += 1
        elif category == "Moderate":
            moderate_count += 1
        else:
            cold_count += 1

    rainy_days, dry_days = count_rainy_and_dry_days(weather_records)

    print("Number of Records:", len(weather_records))
    print("Average Temperature:", round(average_temperature(weather_records), 2), "C")
    print("Maximum Temperature:", max(temperatures), "C")
    print("Minimum Temperature:", min(temperatures), "C")
    print("Average Humidity:", round(sum(humidity_values) / len(humidity_values), 2), "%")
    print("Maximum Humidity:", max(humidity_values), "%")
    print("Minimum Humidity:", min(humidity_values), "%")
    print("Total Rainfall:", total_rainfall(weather_records), "mm")
    print("Average Rainfall:", round(average_rainfall(weather_records), 2), "mm")
    print("Rainy Days:", rainy_days)
    print("Dry Days:", dry_days)
    print("Hot Days:", hot_count)
    print("Moderate Days:", moderate_count)
    print("Cold Days:", cold_count)


def remove_duplicate_temperatures(temperatures):
    """
    Array Concept: Removal of Duplicates from an ordered array.
    First sorts a copy of the list, then removes consecutive duplicates.
    """
    sorted_temps = sorted(temperatures)
    result = []
    for value in sorted_temps:
        if not result or value != result[-1]:
            result.append(value)
    return result


def partition_temperatures(temperatures, pivot):
    """
    Array Concept: Partitioning an array around a pivot value.
    Splits temperatures into those below the pivot and those at or
    above the pivot.
    """
    below = []
    above_or_equal = []
    for value in temperatures:
        if value < pivot:
            below.append(value)
        else:
            above_or_equal.append(value)
    return below, above_or_equal


def kth_smallest_temperature(temperatures, k):
    """Array Concept: Finding the Kth smallest element."""
    sorted_temps = sorted(temperatures)
    return sorted_temps[k - 1]


def array_concepts_demo(weather_records):
    """
    Demonstrates the Array Concepts from the syllabus (Unit V) using
    the temperature values as the example array.
    """
    print("\n--- Array Concepts Demo (using Temperature array) ---")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    temperatures = get_temperature_list(weather_records)
    print("Temperature Array:", temperatures)

    # Traversal
    print("\nTraversal:")
    for temp in temperatures:
        print(temp, end=" ")
    print()

    # Maximum and Minimum
    print("\nMaximum Temperature:", max(temperatures))
    print("Minimum Temperature:", min(temperatures))

    # Sorting
    sorted_temps = sorted(temperatures)
    print("\nSorted Temperatures (Ascending):", sorted_temps)

    # Reverse
    reversed_temps = temperatures[::-1]
    print("Reversed Temperature Array:", reversed_temps)

    # Counting occurrences of a chosen value (first value in list)
    value_to_count = temperatures[0]
    count = temperatures.count(value_to_count)
    print("\nCount of value", value_to_count, "in array:", count)

    # Removal of duplicates
    unique_temps = remove_duplicate_temperatures(temperatures)
    print("\nTemperatures after removing duplicates:", unique_temps)

    # Partitioning around the average value
    pivot = int(sum(temperatures) / len(temperatures))
    below, above_or_equal = partition_temperatures(temperatures, pivot)
    print("\nPartitioning around pivot (average) =", pivot)
    print("Below pivot:", below)
    print("Above or equal to pivot:", above_or_equal)

    # Kth smallest element
    k = get_valid_k(len(temperatures))
    print("\nThe", k, "th smallest temperature is:", kth_smallest_temperature(temperatures, k))


def generate_summary_report(weather_records):
    """
    Module 5 (extended) - Generate a text summary report of the
    weather dataset, combining statistics and classification counts.
    """
    print("\n" + "=" * 55)
    print("             WEATHER DATA SUMMARY REPORT")
    print("=" * 55)

    if len(weather_records) == 0:
        print("No weather records available to generate a report.")
        return

    overall_statistics(weather_records)


    h_date, h_temp, h_hum, h_rain = hottest_day(weather_records)
    c_date, c_temp, c_hum, c_rain = coldest_day(weather_records)
    r_date, r_temp, r_hum, r_rain = day_with_highest_rainfall(weather_records)

    print("\nHottest Day:", h_date, "(", h_temp, "C )")
    print("Coldest Day:", c_date, "(", c_temp, "C )")
    print("Highest Rainfall Day:", r_date, "(", r_rain, "mm )")
    print("=" * 55)


# ======================================================================
# ---- Content originally from main.py ----
# ======================================================================
"""
main.py
--------
Weather Data Analyzer and Statistics System
---------------------------------------------
This is the main program file. It shows the menu, takes the user's
choice, and calls functions from the other modules. This file controls
the overall workflow of the project using loops and conditional
statements (while loop for the menu, if-elif-else for choices).
"""



def sort_records_menu(weather_records):
    """
    Module 9 - Sort Weather Records.
    Lets the user choose to sort by temperature or rainfall.
    """

    print("\n--- Sort Weather Records ---")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    print("1. Sort by Temperature (Ascending)")
    print("2. Sort by Temperature (Descending)")
    print("3. Sort by Rainfall (Ascending)")
    print("4. Sort by Rainfall (Descending)")

    choice = get_valid_menu_choice(1, 4)

    if choice == 1:
        result = sort_records_by_temperature(weather_records, descending=False)
    elif choice == 2:
        result = sort_records_by_temperature(weather_records, descending=True)
    elif choice == 3:
        result = sort_records_by_rainfall(weather_records, descending=False)
    elif choice == 4:
        result = sort_records_by_rainfall(weather_records, descending=True)

    print("\nSorted Records:")
    for record in result:
        print(record)


def hottest_coldest_menu(weather_records):
    """Module 10 - Find Hottest and Coldest Days."""
    print("\n--- Hottest and Coldest Days ---")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    h_date, h_temp, h_hum, h_rain = hottest_day(weather_records)
    c_date, c_temp, c_hum, c_rain = coldest_day(weather_records)

    print("Hottest Day:", h_date, "with", h_temp, "C")
    print("Coldest Day:", c_date, "with", c_temp, "C")


def kth_hottest_coldest_menu(weather_records):
    """Module 11 - Find Kth Hottest/Coldest Day."""
    print("\n--- Kth Hottest/Coldest Day ---")

    if len(weather_records) == 0:
        print("No weather records available.")
        return

    print("1. Find Kth Hottest Day")
    print("2. Find Kth Coldest Day")

    choice = get_valid_menu_choice(1, 2)

    if choice == 1:
        record = kth_hottest_day(weather_records)
        date, temp, hum, rain = record
        print("Kth Hottest Day:", date, "with", temp, "C")
    elif choice == 2:
        record = kth_coldest_day(weather_records)
        date, temp, hum, rain = record
        print("Kth Coldest Day:", date, "with", temp, "C")


def print_menu():
    """Display the main menu."""
    print("\n" + "=" * 50)
    print("           WEATHER DATA ANALYZER")
    print("=" * 50)
    print("1. Add Weather Record")
    print("2. Display All Records")
    print("3. Search Weather Record")
    print("4. Update Weather Record")
    print("5. Delete Weather Record")
    print("6. Temperature Analysis")
    print("7. Rainfall Analysis")
    print("8. Weather Classification")
    print("9. Sort Weather Records")
    print("10. Find Hottest and Coldest Days")
    print("11. Find Kth Hottest/Coldest Day")
    print("12. Weather Statistics")
    print("13. Generate Summary Report")
    print("14. Array Concepts Demo (Bonus)")
    print("15. Exit")
    print("=" * 50)


def main():
    """
    Main function that controls the program using a while loop.
    The loop keeps running until the user chooses to Exit (option 15).
    """
    print("Welcome to the Weather Data Analyzer and Statistics System")

    while True:
        print_menu()
        choice = get_valid_menu_choice(1, 15)

        if choice == 1:
            add_weather_record(weather_records)
        elif choice == 2:
            display_all_records(weather_records)
        elif choice == 3:
            search_weather_record(weather_records)
        elif choice == 4:
            update_weather_record(weather_records)
        elif choice == 5:
            delete_weather_record(weather_records)
        elif choice == 6:
            temperature_analysis_menu(weather_records)
        elif choice == 7:
            rainfall_analysis_menu(weather_records)
        elif choice == 8:
            weather_classification_menu(weather_records)
        elif choice == 9:
            sort_records_menu(weather_records)
        elif choice == 10:
            hottest_coldest_menu(weather_records)
        elif choice == 11:
            kth_hottest_coldest_menu(weather_records)
        elif choice == 12:
            overall_statistics(weather_records)
        elif choice == 13:
            generate_summary_report(weather_records)
        elif choice == 14:
            array_concepts_demo(weather_records)
        elif choice == 15:
            print("\nThank you for using Weather Data Analyzer. Goodbye!")
            break





if __name__ == "__main__":
    main()