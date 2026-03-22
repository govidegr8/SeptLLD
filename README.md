# SeptLLD — Java Low-Level Design Learning Repository

This repository is a Java learning monorepo covering **OOP fundamentals**, **Java advanced concepts**, **multithreading**, **design patterns**, **machine-coding problems**, and a full **Spring Boot booking application**.

---

## Repository Structure

```
SeptLLD/
├── backendlld/          # Java Maven project — learning exercises & machine coding
└── bms2025dec/          # Spring Boot REST API — BookMyShow clone
```

---

## 1. `backendlld` — Java Learning Exercises

A plain Maven Java project (`pom.xml`) organised into three main areas:

### 1.1 OOP Concepts (`oops/`)

#### Bank Account (root `oops/`)
Demonstrates core OOP encapsulation.

| Class | Description |
|---|---|
| `BankAccount` | Bank account with deposit/withdraw |
| `Transaction` | Represents a single bank transaction |
| `Client` | Entry-point that exercises the account |

#### Lab Session 1 — Library Management System (`oops/labsession1/`)
Three milestones building a library system:

| Milestone | Package | Classes |
|---|---|---|
| M1 — Users | `m1` | `User`, `Member`, `Librarian` |
| M2 — Books | `m2` | `Book`, `TextBook`, `NovelBook`, `BookType` (enum), `Lendable` (interface) |
| M3 — System | `m3` | `LibraryManagementSystem`, `Client` |

#### Scaler Tutorials (`oops/scaler/`)
Short focused programs for each OOP topic:

| Topic | Package | Key Classes |
|---|---|---|
| Basic classes | `scaler/` | `Student`, `Batch` |
| Copy Constructor | `scaler/copyconstructor` | `Employee` |
| Inheritance | `scaler/inheritance` | `User` → `Student`, `Instructor`, `Client` |
| Abstract Classes | `scaler/abstractclasseg` | `User` (abstract) → `Student`, `TA`, `Client` |
| Interfaces | `scaler/interfacesEg` | `Stack` (interface), `ArrayListStack`, `LinkedListStack`, `Client` |
| Polymorphism | `scaler/polymorphism` | `Parent`, `Child`, `Client` |

---

### 1.2 Java Advanced Concepts (`oops/scaler/javaAdvancedConcepts/`)

#### Generics (`Generics/`)
| Class | Description |
|---|---|
| `Pair` | Generic pair of two values |
| `SingleDataTypePair` | Pair constrained to one type |
| `Animal`, `Dog`, `Cat` | Type-bounded generics demo |
| `StudentDemo`, `Client` | Usage examples |

#### Exception Handling (`exceptionhandling/`)
Custom checked exceptions: `DuplicationItemException`, `InvalidQuantityException` demonstrated in `Client`.

#### Functional Interfaces & Streams (`functionalInterfaces/`)
| Class | Description |
|---|---|
| `SampleClass` | Demonstrates lambdas with `Function`, `Predicate`, `Consumer` |
| `Client` | Lambda expressions as anonymous class replacements |
| `StreamClient` | Stream API pipelines: `map`, `filter`, `sorted`, `reduce` |
| `Student` | Model used in stream examples |

#### Comparable & Comparator (`labSessionGenerics/comparable/`, `comparator/`)
| Class | Description |
|---|---|
| `PersonV2` | Implements `Comparable<PersonV2>` for natural age ordering |
| `Person` | POJO for comparator examples |
| `PersonAgeComparator` | External `Comparator` by age |
| `PersonNameComparator` | External `Comparator` by name |
| `Client` (both) | Demonstrates `Collections.sort` with each approach |

#### Inventory Management Lab (`labSessionGenerics/InventoryManagement/`)
End-to-end lab session combining Generics, Collections, Comparable, Comparator and Stream API:

| Class | Description |
|---|---|
| `Item` | Abstract base; implements `Comparable` (sorted by price) |
| `Electronics`, `Book`, `Clothing` | Concrete item sub-types |
| `Inventory<T>` | Generic inventory: `add`, `remove`, `getAll` |
| `RecentlyViewItems` | Deque-backed fixed-size recently-viewed list |
| `Order` | Holds `orderId`, `isExpress`, `quantity` |
| `OrderProcessor` | `PriorityQueue`-backed order processing |
| `ItemNameComparator` | Sorts items by name |
| `ItemQuantityComparator` | Sorts items by quantity |
| `Client` | Full demo: add/remove items, sort, filter, recently-viewed, order processing |
| `streamLabSession/Client` | Stream API tasks: map, filter, match, reduce, collect |

---

### 1.3 Multithreading (`oops/scaler/multithreading/`)

| Sub-package | Program | Description |
|---|---|---|
| `introductionToMultithreading` | Hello World & Number Printer | `Thread` and `Runnable`; concurrent hello-world and sequential number printing |
| `syncproblems` | Adder/Subractor | Shows race condition on shared `Count` object |
| `syncMethod` | Adder/Subractor (sync) | Fixes race condition using `synchronized` methods |
| `syncAdderSubractor` | Adder/Subractor (block) | Fixes race condition using `synchronized` blocks |
| `producerconsumer` | Producer–Consumer | Classic bounded-buffer with `wait()`/`notifyAll()` |
| `producerconsumersemaphore` | Producer–Consumer (Semaphore) | Same problem solved with `java.util.concurrent.Semaphore` |
| `multithread_sum_calculation` | Parallel Sum | Splits array across threads using `Callable` + `Future` |
| `callablesAndMergeSort` | Parallel Merge Sort | Recursive parallel merge sort using `ForkJoinPool`/`Callable` |

---

### 1.4 Design Patterns (`designpatterns/`)

#### Singleton (`singletondp/`)
| Class | Variant |
|---|---|
| `DBConnection` | Lazy initialisation (single-threaded) |
| `EagerLoadingDBConn` | Eager (class-load) initialisation |
| `MultithreadedDBConn` | Double-checked locking for thread safety |

#### Factory / Abstract Factory (`factorydp/`)
Implements a Flutter-like cross-platform UI toolkit:

| Class | Description |
|---|---|
| `UIFactory` | Abstract factory interface |
| `AndroidUIFactory` / `IosUIFactory` | Concrete factories |
| `Button`, `Menu` | Abstract product interfaces |
| `AndroidButton`, `AndroidMenu`, `IosButton`, `IosMenu` | Concrete products |
| `UIFactoryFactory` | Factory of factories (selects factory by platform) |
| `Flutter`, `Client` | Consumer of the abstract factory |

#### Builder (`builderdp/`)
`Student` with a static inner `Builder` class; `Client` demonstrates step-by-step object construction.

#### Adapter (`adapterDP/`)
Adapts different bank APIs to a common `BankAPI` interface so PhonePe can call any bank uniformly:

| Class | Description |
|---|---|
| `BankAPI` | Target interface |
| `HdfcBank`, `YesBank` | Adaptees (incompatible signatures) |
| `HdfcBankAdapter`, `YesBankAdapter` | Adapters bridging to `BankAPI` |
| `PhonePe`, `Client` | Consumer and demo |

#### Observer (`observerDP/`)
Amazon order-placed event system:

| Class | Description |
|---|---|
| `Amazon` | Subject; manages subscriber list |
| `OrderPlacedSubscriber` | Observer interface |
| `NotifyCustomerSubscriber` | Sends customer notification |
| `NotifySellerSubscriber` | Alerts the seller |
| `DeliveryOptionsSubscriber` | Triggers delivery options |
| `Client` | Wires everything and places an order |

#### Decorator (`decoratorDP/`)
Ice-cream cone topping system:

| Class | Description |
|---|---|
| `IceCreamConeConstituents` | Component interface (cost, description) |
| `ChocoChips` | Decorator adding chocolate chips |
| `OrangeScoop` | Decorator adding an orange scoop |
| `Client` | Builds and prices composed ice creams |

#### Prototype & Registry (`prototypeAndRegistry/`)
| Class | Description |
|---|---|
| `Prototype` | Cloneable marker interface |
| `Student` | Concrete prototype |
| `IntelligentStudent` | Extended student prototype |
| `StudentRegistry` | Registry mapping type keys to prototypes |
| `Database`, `Client` | Simulate bulk creation via cloning |

---

### 1.5 Machine Coding (`machinecoding/`)

#### Parking Lot System (`parkinglot/`)
Production-style parking lot with:

| Layer | Classes |
|---|---|
| Models | `ParkingLot`, `ParkingFloor`, `ParkingSpot`, `EVParkingSpot`, `Gate`, `Ticket`, `Bill`, `Vehicle`, `Operator`, `Meter`, `Consumption`, `Payment` |
| Enums | `ParkingLotStatus`, `GateStatus`, `GateType`, `ParkingSpotStatus`, `VehicleType`, `PaymentMode`, `PaymentStatus`, `BillStatus`, `SpotAssignmentStrategyType`, `FeesCalculatorStrategyType` |
| Service interfaces | `iParkingLotService`, `iTicketService` |
| Service impls | `ParkingLotServiceImpl`, `TicketServiceImpl` |
| Strategies | `iSpotAssignmentStrategy`, `RandomSpotAssignmentStrategy` |
| Controllers | `ParkingLotController`, `TicketController` |
| DTOs | `ParkingLotRequestDTO`, `ParkingLotResponseDTO`, `TicketRequestDTO`, `TicketResponseDTO` |
| Repositories | `ParkingLotRepo`, `TicketRepo`, `GateRepo` |
| Translators | `ParkingLotTranslator`, `TicketTranslator` |
| Entry point | `Driver` |

#### Tic-Tac-Toe (`tictactoe/`)
Console game supporting human vs. human or human vs. bot:

| Layer | Classes |
|---|---|
| Models | `Game`, `Board`, `Cell`, `Player`, `Bot`, `Move`, `CellState` (enum), `GameState` (enum), `PlayerType` (enum), `DifficultyLevel` (enum) |
| Strategies | `WinningStrategy`, `RowWinningStrategy`, `ColumnWinningStrategy`, `DiagonalWinningStrategy` |
| Bot strategies | `BotPlayingStrategy`, `EasyBotPlayingStrategy`, `MediumBotPlayingStrategy`, `HardBotPlayingStrategy` |
| Controller | `GameController` |
| Exceptions | `DuplicateSymbolException`, `PlayerValidationException` |
| Entry point | `Driver` |

---

## 2. `bms2025dec` — BookMyShow Spring Boot Application

A REST API backend for a movie ticket booking system, built with **Spring Boot**, **Spring Data JPA**, **Spring Security**, and **MySQL**.

### Models

| Model | Description |
|---|---|
| `User` | Registered user |
| `Movie` | Movie with actors and features |
| `Actor` | Actor entity |
| `Theatre` | Theatre in a city |
| `Screen` | Screen inside a theatre |
| `Seat` | Physical seat in a screen |
| `SeatType` | Enum: GOLD, SILVER, DIAMOND, etc. |
| `Show` | A specific screening (movie + screen + time) |
| `SeatTypeShow` | Pricing per seat type for a show |
| `ShowSeat` | Booking status of each seat in a show |
| `ShowSeatStatus` | Enum: AVAILABLE, LOCKED, BOOKED |
| `Booking` | Booking record linking user, show and seats |
| `BookingStatus` | Enum: PENDING, CONFIRMED, CANCELLED |
| `Payment` | Payment record for a booking |
| `PaymentMethodType` | Enum: CREDIT_CARD, DEBIT_CARD, UPI, etc. |
| `PaymentStatus` | Enum: PENDING, COMPLETED, FAILED |
| `City` | City entity for theatres |
| `Feature` | Movie feature (3D, IMAX, etc.) |

### REST Endpoints

| Controller | Endpoint | Description |
|---|---|---|
| `UserController` | `POST /users` | Register a new user |
| `BookingController` | `POST /bookings` | Book seats for a show |

### Key Implementation Highlights
- **Thread-safe booking** via `ReentrantLock` (injected as a Spring bean from `ReentrantLockBean`) to prevent double-booking the same seat.
- **Custom exceptions**: `SeatNotAvailableException`, `ShowDoesNotExistException`, `UserDoesNotExistException`, `BadRequestException`.
- **DTO pattern**: `BookingRequestDTO`/`BookingResponseDTO`, `UserRequestDTO`/`UserResponseDTO`, `SeatDTO`, `ErrorDTO`.
- **Translators**: `BookingTranslator`, `UserTranslator` convert between models and DTOs.
- **Spring Security** configured in `SecurityConfig`.
- Database: MySQL at `jdbc:mysql://127.0.0.1:3306/bookmyshowdec2025`, port `8081`.

### Running the Application
```bash
cd bms2025dec
./mvnw spring-boot:run
```

---

## Technology Stack

| Area | Technology |
|---|---|
| Language | Java 17+ |
| Build tool | Maven (`pom.xml`) |
| Web framework | Spring Boot 3.x (bms2025dec) |
| Persistence | Spring Data JPA + Hibernate |
| Database | MySQL |
| Security | Spring Security |
| Concurrency | `java.util.concurrent` (Semaphore, Callable, Future, ReentrantLock) |
