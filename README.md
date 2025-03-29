# 🚀 Requirement Tool: REST Controller Generator

## 📌 Project Target
- **Project:** pb360-STI
- **Database:** DB2 EXCEEDDB

## 🛠️ Purpose
This tool is designed to generate a REST controller by reading parameters from the UI, extracting data from a JSON file, and writing the output accordingly.

## 🔹 Input & Output
- **Input:** Controller Name (String), Controller URL (String)
- **Output:** Auto-generated common files based on the structured REST Controller architecture

## 📂 REST Controller Structure
```
Application:
├── Securities Validator
│   ├── STI Rest API
│   │   ├── Controller
│   │   ├── Model
│   │   ├── Service
│   │   │   └── ServiceImpl
│   │   ├── Validator
│   │   ├── Options
│   │
│   ├── Test
│   │   ├── ControllerTest
```

## 📑 Detailed Breakdown
### 1️⃣ Controller File (`pb360.controller`)
- **Annotation:** `@RestController` with `@RequestMapping(value = "URL")`
- **Dependencies:** Uses `@Autowired` for validation, service, and options
- **Methods:** Implements six standard REST methods: `GET`, `GET ALL`, `POST`, `PATCH`, `DELETE`, `OPTIONS`
- **Naming Convention:** Function names follow `{functionPrefix}{ControllerName}`
- **Annotations:**
  ```java
  @UserAuthorization("functionName + ControllerName")
  @RequestMapping(method = {POST, GET, DELETE, PATCH, OPTIONS})
  ```
- **Static Variables:**
  ```java
  private static final int INITIAL_PAGE = 1;
  private static final int INITIAL_PAGE_SIZE = 10;
  ```

### 2️⃣ Model File (`pb360.model`)
- Java class named after the controller
- Extends `ResourceSupport (hateoas)`
- Contains a default constructor

### 3️⃣ Validator File (`pb360.validation`)
- Annotated with `@Component`
- Implements Spring `Validator` and overrides all required methods

### 4️⃣ Options File (`pb360.service.options`)
- Extends `AbstractOptionsImpl (core)` and implements `OptionsService (core)`
- Overrides all `OptionsService` methods with empty function bodies
- Contains default methods to read JSON files

### 5️⃣ Service File (`pb360.service`)
- Java interface defining five standard methods: `{functionName}{ControllerName}`
- Supports JSON file reading

### 6️⃣ Unit Test File (`pb360.controller.test`)
- Java class implementing `SpringJUnit4Test`
- Includes test cases for JSON file processing

---

This structured approach ensures efficient development while maintaining best practices. 🚀

