# ArWikiCats - Wikipedia Category Translation System

## Overview

ArWikiCats is an integrated system for translating English Wikipedia category names into standardized Arabic names. The system consists of three interconnected repositories that work together to provide a comprehensive solution:

1. **ArWikiCats** - Core Python library
2. **ArWikiCatsWeb** - Web UI and REST API
3. **cats_maker_new** - Wikipedia bot application

## Repositories

### 1. ArWikiCats (Core Python Library)

**Role**: Core logic for translating category names

**Functions**:
- Translate Wikipedia category names from English to Arabic
- Standardize and normalize Arabic category names
- Provide a programming interface (API) for use in other applications
- Contains no user interface or network connections

**Output**:
- Installable Python package
- Can be used as a library in other projects

**Dependencies**:
- Does not depend on other repositories
- Works as a standalone module

---

### 2. ArWikiCatsWeb (Web UI and API)

**Role**: Provide web interface and REST API for ArWikiCats functionality

**Functions**:
- Interactive web interface for end users
- REST API over HTTP
- Access translation features from browser or via HTTP requests
- Process requests and return results in JSON format

**Output**:
- Deployable web application
- REST API endpoints

**Dependencies**:
- **Depends on**: ArWikiCats (uses it as a library)
- Imports and uses translation functions from ArWikiCats

---

### 3. cats_maker_new (Wikipedia Bot)

**Role**: Automated bot for translating and creating categories on Arabic Wikipedia

**Functions**:
- Extract category names from English Wikipedia
- Use ArWikiCats to translate category names
- Automatically create translated categories on Arabic Wikipedia
- Batch processing of categories

**Output**:
- New categories on Arabic Wikipedia
- Operation logs and reports

**Dependencies**:
- **Depends on**: ArWikiCats (uses it as a library)
- Imports and uses translation functions from ArWikiCats
- Interacts with Wikipedia API

## Data Flow

```
+------------------+
| English          |
| Wikipedia        |
+--------+---------+
         |
         | English category names
         v
+--------+---------+
|  ArWikiCats      |  <---- Core logic
|  (Python Library)|
+--------+---------+
         |
         | Arabic category names (standardized)
         |
         +------------------------+------------------------+
         |                        |                        |
         v                        v                        v
+--------+---------+     +--------+---------+     +--------+---------+
| ArWikiCatsWeb    |     | cats_maker_new   |     | Other apps       |
| (Web UI)         |     | (Bot)            |     | (future)         |
+------------------+     +--------+---------+     +------------------+
         |                        |
         v                        v
+--------+---------+     +--------+---------+
| End users        |     | Arabic Wikipedia |
| via browser      |     | (new categories) |
+------------------+     +------------------+
```

## Relationships and Dependencies

### Hierarchical Structure:

1. **Core Layer**: ArWikiCats
   - Does not depend on any other repository
   - Provides core functionality for all applications

2. **Application Layer**: ArWikiCatsWeb and cats_maker_new
   - Both depend on ArWikiCats
   - Use the same core logic
   - Independent of each other

### Dependency Direction:

```
ArWikiCats  (Base - no dependencies)
    ↑
    |
    +------------+------------+
    |            |            |
ArWikiCatsWeb   cats_maker_new   (Applications - depend on base)
```

## Use Cases

### Scenario 1: End user using web interface
1. User opens ArWikiCatsWeb in browser
2. User enters English category name
3. ArWikiCatsWeb calls ArWikiCats for translation
4. ArWikiCats returns translated Arabic name
5. ArWikiCatsWeb displays result to user

### Scenario 2: Bot creates categories on Wikipedia
1. cats_maker_new extracts category list from English Wikipedia
2. For each category, calls ArWikiCats for translation
3. ArWikiCats returns translated Arabic names
4. cats_maker_new checks if category exists on Arabic Wikipedia
5. If not present, creates new category

### Scenario 3: External application using REST API
1. Application sends HTTP request to ArWikiCatsWeb
2. ArWikiCatsWeb calls ArWikiCats for translation
3. ArWikiCats returns result
4. ArWikiCatsWeb sends response as JSON
5. Application uses translated data

## Technical Architecture

### ArWikiCats (Core Library)
- **Language**: Python
- **Type**: Library/Package
- **Interface**: Programming API
- **Deployment**: PyPI or local installation

### ArWikiCatsWeb (Web Interface)
- **Language**: Python (with web framework)
- **Type**: Web application
- **Interface**: HTTP/REST API + User interface
- **Deployment**: Web server

### cats_maker_new (Bot)
- **Language**: Python
- **Type**: Command-line application/service
- **Interface**: Command line
- **Deployment**: Scheduled or continuous execution

## Key Advantages of This Architecture

1. **Separation of Concerns**: Each repository has a clear and defined role
2. **Reusability**: Core logic in ArWikiCats can be used by multiple applications
3. **Ease of Maintenance**: Changes to core logic happen in one place
4. **Scalability**: New applications can use ArWikiCats without modifying the core library
5. **Independence**: ArWikiCatsWeb and cats_maker_new are independent of each other

## Development and Contribution

When developing or maintaining this system:

1. **For changes in translation logic**: Modify ArWikiCats
2. **For changes in web interface or API**: Modify ArWikiCatsWeb
3. **For changes in bot behavior**: Modify cats_maker_new

**Important Note**: Any update to ArWikiCats may require updating ArWikiCatsWeb and/or cats_maker_new to use the new version.

## Links

- [ArWikiCats - Core Library](https://github.com/ArWikiCats/ArWikiCats)
- [ArWikiCatsWeb - Web Interface](https://github.com/ArWikiCats/ArWikiCatsWeb)
- [cats_maker_new - Bot](https://github.com/ArWikiCats/cats_maker_new)

---

*For the Arabic version of this document, see [README.md](README.md)*
