# CSA09 – Assignment 4 (Java)

**Register number:** 192524480  
**Language:** Java (JDK 17 recommended)

This repository contains the task-wise solutions and design notes for Assignment 4.

## Task-wise files

| Task | Topic | Files |
|---|---|---|
| 1 | GUI design review and improved fee-payment design | [DesignReview.md](Task01/DesignReview.md), [FeeWindow.java](Task01/FeeWindow.java), [FeeService.java](Task01/FeeService.java) |
| 2 | Hospital outpatient appointment desk – event model and design | [EventDesign.md](Task02/EventDesign.md) |
| 3 | Campus library search GUI | [LibrarySearchScreen.java](Task03/LibrarySearchScreen.java) |
| 4 | AWT mouse events and drawing pad | [DrawPad.java](Task04/DrawPad.java) |
| 5 | Currency converter and event-handling styles | [Converter.java](Task05/Converter.java), [ConverterFrameListener.java](Task05/ConverterFrameListener.java), [ConverterNamedInner.java](Task05/ConverterNamedInner.java), [ConverterAnonymous.java](Task05/ConverterAnonymous.java), [ConverterStyles.md](Task05/ConverterStyles.md) |
| 6 | Campus event registration – JDBC and Swing GUI | [EventRegistrationApp.java](Task06/EventRegistrationApp.java), [schema.sql](Task06/schema.sql) |

## Compile and run

Open a terminal in the folder containing the Java file.

```bash
javac FileName.java
java ClassName
```

Examples:

```bash
cd Task03
javac LibrarySearchScreen.java
java LibrarySearchScreen
```

```bash
cd Task04
javac DrawPad.java
java DrawPad
```

```bash
cd Task05
javac Converter.java
java Converter
```

## Task 1 – Fee payment database setup

The GUI and service expect a MySQL database and a table named `fees`. Create it before running:

```sql
CREATE DATABASE campus_events;
USE campus_events;
CREATE TABLE fees (
    id INT PRIMARY KEY AUTO_INCREMENT,
    reg_no VARCHAR(20) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    paid_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

Add the MySQL Connector/J driver to the classpath. Configure `DB_URL`, `DB_USER`, and `DB_PASSWORD` environment variables. Example URL: `jdbc:mysql://localhost:3306/campus_events`.

Compile both files together:

```bash
javac FeeService.java FeeWindow.java
java FeeWindow
```

## Task 6 – Event registration database setup

1. Run [schema.sql](Task06/schema.sql) in MySQL.
2. Add MySQL Connector/J to the classpath.
3. Set `DB_URL`, `DB_USER`, and `DB_PASSWORD` environment variables (defaults are localhost, root, and an empty password).
4. Compile and run:

```bash
javac -cp .;mysql-connector-j.jar EventRegistrationApp.java
java -cp .;mysql-connector-j.jar EventRegistrationApp
```

On macOS/Linux, replace the classpath separator `; ` with `:` (without the space).

## Before submission

- Run each program in your own Java environment and capture screenshots of actual output.
- Test valid and invalid input paths and record observed behaviour.
- For database tasks, include your own database setup and successful query/result screenshots.
- Review the written analysis against your assignment rubric and add any required diagrams, comparison tables or evidence not represented by the source files.

**Note:** Exchange rates in the currency converter are demonstration constants, not live market rates. The library search screen uses sample in-memory results. The GUI/database tasks need the stated local database setup and driver. Do not report a successful database execution until you have run it locally.
