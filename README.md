Project Philosophy

    Red-XAI Easy Functions is an evolving utility module crafted alongside the development of my personal and professional Python projects. Rather than relying on repetitive boilerplate or reinventing the wheel for common tasks, this module aims to simplify and abstract core operations like file handling, JSON manipulation, path resolution, and project structuring.

    As my projects grow in scale and complexity, I continuously identify areas where standard Python functionality can be made more intuitive, flexible, and developer-friendly. Each function in this toolkit reflects a real-world use case I've encountered—whether automating project setup, safely navigating file systems, or dynamically working with configuration files.

    This module is built to be clean, scalable, and adaptable—making basic Python workflows faster, more readable, and easier to integrate across a wide variety of project types.


# 🔧 Red-XAI Easy Functions

**Red-XAI Easy Functions** is a powerful and flexible Python toolkit developed by [Red-XAI](https://github.com/MainDirectory) to simplify common development tasks such as file management, JSON operations, path resolution, project structuring, and random number generation.
=
This library is designed for developers who want concise, reusable, and readable utility functions without reinventing the wheel every time.

---

## 🧠 Project Philosophy

**Red-XAI Easy Functions** is an evolving utility module crafted alongside the development of my personal and professional Python projects. Rather than relying on repetitive boilerplate or rewriting standard patterns for common tasks, this toolkit simplifies and abstracts essential operations like file handling, JSON manipulation, and dynamic path resolution.

As my projects grow in scale and complexity, I identify pain points in Python's default utilities and convert those patterns into **flexible, reusable functions**. This module is clean, scalable, and adaptable—empowering developers to write more with less, and integrate powerful tools into any Python project quickly.

---

## 📦 Installation

Install directly from PyPI:

```python
pip install RedXAIEasyFunctions

##Import into your code:

from redxaieasyfunctions import *

#📚 Full Function Reference & Usage Examples

##Below is a comprehensive reference of all available functions with usage examples and expected behavior.
🔍 LocalizPath(filename: str) -> str

#Searches recursively from the current working directory to find a specific file. Returns the absolute path to its root folder.

root = LocalizPath("installer.cfg")

#Raises:

#    FileNotFoundError if file not found

#    RuntimeError if multiple matches found

#🔎 LocalSearch(local_path: str, search_string: str, secure_search: bool = True) -> str

#Constructs a path from a base directory using dot (LP.) or plus (LP+) syntax.

file_path = LocalSearch(root, "LP.assets.config.settings.json")
parent_file = LocalSearch(root, "LP+data+myfile.json")

#Raises:

    #ValueError if LP syntax is invalid

    #FileNotFoundError if path doesn't exist and secure_search=True

#📄 LoadJson(path: str) -> dict

#Loads a .json file into a Python dictionary.

data = LoadJson("config.json")

#Raises:

#    FileNotFoundError if file doesn't exist

#    json.JSONDecodeError if content is invalid

#📊 JSEasySearch(json_data: dict, table_path: str, key, value_indices: str) -> list | any

#Searches deeply nested JSON using dot syntax and returns specified indexed values from a list.

values = JSEasySearch(data, "Symbols.Runes", "Main", "1/3")

#Raises:

#    KeyError or IndexError internally if path or key doesn't exist

#✏️ JSEasyChange(json_data: dict, table_path: str, key, index: int, new_value) -> None

#Changes a list value or key in a nested dictionary by index.

JSEasyChange(data, "Runes.Symbols", "Alpha", 2, "Ω")

#Raises:

#    KeyError or IndexError on invalid paths or indices

#➕ JSEasyAdd(json_data: dict, table_path: str, key, new_value) -> None

#Adds a value to a list or creates a new list for a key.

JSEasyAdd(data, "Runes.Symbols", "Alpha", "*")

#Raises:

#   KeyError if table path doesn't exist

#➖ JSEasyRemove(json_data: dict, table_path: str, key, index: int) -> None

#Removes a value by index from a list in a nested JSON structure.

JSEasyRemove(data, "Runes.Symbols", "Alpha", 1)

#Raises:

#    IndexError if index is out of range

#    KeyError if path or key is invalid

#💾 JSEasySave(json_data: dict, path: str) -> None

#Writes the modified dictionary back to a file with pretty indentation.

JSEasySave(data, "updated.json")

#Raises:

#    IOError or PermissionError on file issues

#📂 JSEasyJsonCreate(path: str, filename: str) -> None

#Creates an empty JSON file at a target path.

JSEasyJsonCreate("settings", "default_config")

#Raises:

#    OSError if path is invalid

#📄 EasyFileCreate(path: str, filename: str) -> None

#Creates a blank file with .txt if no extension is given.

EasyFileCreate("logs", "startup_log")

#Raises:

#    OSError if path is invalid or write fails

#📁 EasyFolderCreate(path: str, foldername: str) -> None

#Creates a new directory if it doesn't already exist.

EasyFolderCreate("resources", "fonts")

#Raises:

#    OSError on invalid or locked directories

#📦 EasyZip(folder_path: str) -> None

#Zips an entire folder into a .zip file.

EasyZip("build_output")

#Raises:

#    ValueError if folder is empty

#    OSError if folder doesn't exist

🌳 EasyProjectTree(project_path: str, tree_file_name: str) -> None

#Generates a visual .txt representation of the project directory.

EasyProjectTree(".", "DirectoryTree.txt")

#Output:

#📁 root_folder
#    📁 assets
#        📄 logo.png
#    📁 config
#        📄 settings.json
#    📄 main.py

#Raises:

#    OSError if write path is invalid

#🎲 EasyRandom() -> int

#Returns a pseudo-random digit from 0 to 9 using time-based entropy.

number = EasyRandom()

#Raises:

#    None

#🎲 EasyRandomPlus(as_string: bool, amount: int) -> str | list[int]

Generates a string or list of pseudo-random digits.

EasyRandomPlus(True, 6)  # "392104"
EasyRandomPlus(False, 4) # [3, 9, 2, 1]

#Raises:

#    ValueError if amount is negative

#📦 EasyJSTable(json_data: dict, table_name: str) -> None

Ensures a dictionary table exists in a JSON object.

EasyJSTable(data, "Runes")

#Raises:

#    None

#🗝️ EasyJSKey(json_data: dict, table, key_or_bulk: str, values: str = None, is_multi: bool = False) -> None

#Adds keys and values to a JSON table, either single or multi-key.

# Single
EasyJSKey(data, "Runes", "Symbols", "α/β/γ")

# Multiple
EasyJSKey(data, "Runes", "UpperCase=A/B/C;LowerCase=a/b/c", is_multi=True)

#Raises:

#    ValueError if table is not a string, int, or dict

#⚙️ _parse_value_string(value_string: str) -> list

Parses strings like "true/123/[1,2]" into a list of typed values. (Used internally)

_parse_value_string("true/4.5/[1,2,3]")  # [True, 4.5, [1, 2, 3]]

#Raises:

#    None (handles eval fallback)

# 🔄 Efficient Function Embedding & Superiority Breakdown

# The following examples show how to **efficiently chain or embed** functions together from this module,
# and explain **why** certain functions outperform or replace native Python workflows.

# 1️⃣ Combine: LocalizPath + LocalSearch + LoadJson
# Efficient for dynamically locating project files anywhere on disk.

# Instead of hardcoding JSON paths:
# Traditional Way:
# config_path = "C:/project/assets/config/settings.json"
# with open(config_path) as f:
#     data = json.load(f)

# With this module:
root = LocalizPath("installer.cfg")
json_path = LocalSearch(root, "LP.assets.config.settings.json")
data = LoadJson(json_path)

# Explanation:
# This combo allows you to dynamically locate any file without hardcoding paths.
# It is especially useful when moving between environments, deployments, or machines.
# LocalSearch supports both relative and upward traversal, replacing fragile os.path.join() trees.

# ✅ Superior to: os.path.join(), manual file lookups, fragile open() calls.

# ------------------------------------------------------------

# 2️⃣ Combine: EasyProjectTree + LocalizPath
# Automatically visualize a project from its dynamic root.

EasyProjectTree(LocalizPath("installer.cfg"), "MyProjectStructure.txt")

# Explanation:
# Instead of manually writing custom directory walkers for logging or debugging,
# this combo provides a plug-and-play way to generate an overview of your entire folder system.

# ✅ Superior to: Manual os.walk + nested print() or file.write()

# ------------------------------------------------------------

# 3️⃣ Combine: LoadJson + JSEasyAdd + JSEasySave
# Append to a JSON array and save cleanly.

data = LoadJson("Directory.json")
JSEasyAdd(data, "Runes.Symbols", "Main", "🜁")
JSEasySave(data, "Directory.json")

# Explanation:
# Compared to standard Python methods, you no longer need to:
# - try/except KeyError
# - check if keys exist
# - check if values are lists
# - manually reopen and save the file

# ✅ Superior to: json.load + if key in + append + json.dump boilerplate

# ------------------------------------------------------------

# 4️⃣ Combine: EasyRandomPlus + EasyJSKey
# Generate secure-looking entropy keys and inject them directly into JSON.

rand_key = EasyRandomPlus(True, 12)
EasyJSKey(data, "Keys", "GeneratedKey", rand_key)

# Explanation:
# This replaces needing random or secrets modules,
# and can quickly generate bulk numeric keys as strings for API use, UID tokens, or short codes.

# ✅ Superior to: random.randint loops or UUIDs when only digits are needed

# ------------------------------------------------------------

# 5️⃣ Combine: EasyFileCreate + EasyFolderCreate + EasyJsonCreate
# Set up an entire structure in 3 lines — ideal for initializing new projects.

EasyFolderCreate(".", "MyApp")
EasyFileCreate("./MyApp", "readme.txt")
JSEasyJsonCreate("./MyApp", "config")

# Explanation:
# This approach removes the need to wrap each call in try/except blocks
# and avoids manual path checks with os.path.exists().

# ✅ Superior to: os.makedirs + open() boilerplate with permission handling

# ------------------------------------------------------------

# 6️⃣ Combine: EasyJSTable + EasyJSKey + JSEasyAdd + JSEasySave
# Build a full nested structure with fallback safety

EasyJSTable(data, "Symbols")
EasyJSKey(data, "Symbols", "Letters", "A/B/C")
JSEasyAdd(data, "Symbols", "Letters", "D")
JSEasySave(data, "Directory.json")

# Explanation:
# Together these eliminate the need for:
# - checking if tables (keys) exist
# - managing list append logic
# - catching missing key errors
# - reopening and rewriting files

# ✅ Superior to: Standard nested dict + list setup using get(), setdefault(), or defaultdict()

# ------------------------------------------------------------

# 7️⃣ Combine: LocalSearch + EasyZip
# Zip a folder dynamically located by name

root = LocalizPath("installer.cfg")
target_folder = LocalSearch(root, "LP.assets.configs")
EasyZip(target_folder)

# Explanation:
# This combo lets you find a project-relative folder anywhere and instantly compress it without temp paths.

# ✅ Superior to: Manual os.walk + zipfile.ZipFile calls + custom path validation


*

```
📖 License

MIT License — Free to use for personal, open-source, or commercial projects.

MIT License

Copyright (c) 2025 MainDirectory

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...

🔗 Links

    GitHub: github.com/MainDirectory/RedXEasyFunctions

    PyPI: pypi.org/project/RedXAIEasyFunctions

💬 Need Help?

Open an issue or discussion on GitHub. Contributions and suggestions are welcome!



Chat

