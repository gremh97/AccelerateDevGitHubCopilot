# Library App

## Description

Library App is a C# application designed to manage a collection of books, users, and borrowing activities. It provides a simple interface for adding, searching, and lending books, as well as managing user accounts.

## Project Structure

- **src/**
  - **Library.ApplicationCore/**  
    Core business logic, domain entities, enums, and interfaces.
    - `Entities/`  
      - `Book.cs`: Book domain model  
      - `BookItem.cs`: Physical copy of a book  
      - `Author.cs`: Author domain model  
      - `Patron.cs`: Library user domain model  
      - `Loan.cs`: Book loan domain model  
    - `Enums/`  
      - `LoanReturnStatus.cs`, `LoanExtensionStatus.cs`, `MembershipRenewalStatus.cs`: Status enums for operations  
      - `EnumHelper.cs`: Utility for enum descriptions  
    - `Interfaces/`  
      - `IBookRepository.cs`, `IPatronRepository.cs`, `ILoanRepository.cs`: Data access contracts  
      - `ILoanService.cs`, `IPatronService.cs`: Service contracts  
    - `Services/`  
      - `LoanService.cs`: Business logic for loans  
      - `PatronService.cs`: Business logic for patrons  
  - **Library.Infrastructure/**  
    Data access implementations (JSON-based repositories).
    - `Data/`  
      - `JsonData.cs`: Loads and saves data from JSON files  
      - `JsonPatronRepository.cs`, `JsonLoanRepository.cs`: Repository implementations  
  - **Library.Console/**  
    Console UI and application entry point.
    - `Program.cs`: Application startup and DI setup  
    - `ConsoleApp.cs`: Main console loop and UI logic  
    - `CommonActions.cs`, `ConsoleState.cs`: UI enums  
    - `Json/`: JSON data files (`Books.json`, `Authors.json`, etc.)  
    - `appSettings.json`: Configuration for JSON paths  
- **tests/**
  - **UnitTests/**  
    Unit tests for core services and repositories.
    - `ApplicationCore/LoanService/`, `ApplicationCore/PatronService/`: Test classes for service logic  
    - `LoanFactory.cs`, `PatronFactory.cs`: Test data factories  
- **.github/workflows/**  
  - `build-test.yml`: GitHub Actions workflow for CI

---

## Key Classes and Interfaces

- **Entities**
  - [`Book`](src/Library.ApplicationCore/Entities/Book.cs): Represents a book, including title, author, genre, ISBN, and cover image.
  - [`BookItem`](src/Library.ApplicationCore/Entities/BookItem.cs): Represents a physical copy of a book, with acquisition date and condition.
  - [`Author`](src/Library.ApplicationCore/Entities/Author.cs): Represents an author with an ID and name.
  - [`Patron`](src/Library.ApplicationCore/Entities/Patron.cs): Represents a library user, including membership info and current loans.
  - [`Loan`](src/Library.ApplicationCore/Entities/Loan.cs): Represents a book loan, including due/return dates and references to book and patron.

- **Enums**
  - [`LoanReturnStatus`](src/Library.ApplicationCore/Enums/LoanReturnStatus.cs), [`LoanExtensionStatus`](src/Library.ApplicationCore/Enums/LoanExtensionStatus.cs), [`MembershipRenewalStatus`](src/Library.ApplicationCore/Enums/MembershipRenewalStatus.cs): Indicate the result of service operations.
  - [`EnumHelper`](src/Library.ApplicationCore/Enums/EnumHelper.cs): Utility for getting enum descriptions.

- **Interfaces**
  - [`IBookRepository`](src/Library.ApplicationCore/Interfaces/IBookRepository.cs): Contract for book data access (not shown in this excerpt).
  - [`IPatronRepository`](src/Library.ApplicationCore/Interfaces/IPatronRepository.cs): Contract for patron data access.
  - [`ILoanRepository`](src/Library.ApplicationCore/Interfaces/ILoanRepository.cs): Contract for loan data access.
  - [`ILoanService`](src/Library.ApplicationCore/Interfaces/ILoanService.cs): Contract for loan-related business logic.
  - [`IPatronService`](src/Library.ApplicationCore/Interfaces/IPatronService.cs): Contract for patron-related business logic.

- **Services**
  - [`LoanService`](src/Library.ApplicationCore/Services/LoanService.cs): Implements business logic for returning and extending loans.
  - [`PatronService`](src/Library.ApplicationCore/Services/PatronService.cs): Implements business logic for renewing patron memberships.

- **Infrastructure**
  - [`JsonData`](src/Library.Infrastructure/Data/JsonData.cs): Loads and saves entities from JSON files.
  - [`JsonPatronRepository`](src/Library.Infrastructure/Data/JsonPatronRepository.cs): Patron repository using JSON storage.
  - [`JsonLoanRepository`](src/Library.Infrastructure/Data/JsonLoanRepository.cs): Loan repository using JSON storage.

- **Console UI**
  - [`ConsoleApp`](src/Library.Console/ConsoleApp.cs): Main console application loop and UI logic.
  - [`CommonActions`](src/Library.Console/CommonActions.cs), [`ConsoleState`](src/Library.Console/ConsoleState.cs): Enums for UI state and actions.

- **Tests**
  - Unit tests are located in [tests/UnitTests/](tests/UnitTests/) and cover service logic and repository behavior using test data factories.

## Usage

1. Clone the repository.
2. Open the solution in Visual Studio or your preferred C# IDE.
3. Build the project.
4. Run the application using the IDE or `dotnet run` from the command line.
5. Follow the on-screen instructions to interact with the library system.

## License

This project is licensed under the MIT License.
