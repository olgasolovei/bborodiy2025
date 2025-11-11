# UML-діаграма класів та опис відповідності принципам SOLID

---

## Загальна архітектура

Система розбита на три рівні:

* **Presentation Layer (UI / Web)** — компоненти для взаємодії з користувачем;
* **Domain Layer (Business Logic)** — логіка моніторингу, AI-аналізу, оповіщення;
* **Data Layer (IoT & Storage)** — сенсори, сховище даних, зв’язок із Azure.

---

## UML-Діаграма класів

```plantuml
@startuml
skinparam classAttributeIconSize 0
skinparam classFontColor #333333
skinparam classBackgroundColor #F8FAFF
skinparam classBorderColor #3366CC
skinparam titleBorderRoundCorner 15
skinparam titleBorderColor #3366CC

title UML Class Diagram – AI + IoT Crane Monitoring System

package "Presentation Layer" #E6F0FF {
  class DashboardController {
    +displayCraneStatus()
    +showAlerts()
    +showReports()
  }

  class ReportController {
    +generateReport(period)
    +exportReport(format)
  }

  class UserController {
    +login(email, password)
    +createUser()
    +assignRole()
  }
}

package "Domain Layer" #E8FFF0 {
  class Crane {
    -id : int
    -name : string
    -maxLoad : double
    -currentLoad : double
    +isOverloaded() : bool
  }

  class IoTDevice {
    -deviceId : string
    -status : string
    +sendTelemetry()
    +reconnect()
  }

  class TelemetryData {
    -timestamp : datetime
    -loadValue : double
    -craneId : int
  }

  class AIAnalyzer {
    +analyze(data : TelemetryData) : RiskLevel
    +predictOverload() : bool
  }

  class Alert {
    -id : int
    -craneId : int
    -riskLevel : RiskLevel
    -timestamp : datetime
    +notifyUser()
  }

  class NotificationService {
    +sendEmail(user : User, alert : Alert)
    +sendDashboardAlert(alert : Alert)
  }

  class ReportGenerator {
    +generateSummary(period)
    +calculateAIMetrics()
  }
}

package "Data Layer" #FFF8E6 {
  class DatabaseManager {
    +saveTelemetry(data : TelemetryData)
    +getCraneHistory(craneId)
    +saveAlert(alert : Alert)
  }

  class IoTHubConnector {
    +receiveData()
    +sendCommand()
  }
}

package "Entities" #F3F3F3 {
  class User {
    -id : int
    -name : string
    -email : string
    -role : UserRole
  }

  enum UserRole {
    Administrator
    SafetyEngineer
    CraneOperator
    ProjectManager
  }

  enum RiskLevel {
    NORMAL
    WARNING
    CRITICAL
  }
}

' --- Зв’язки ---
UserController --> User
DashboardController --> Crane
DashboardController --> Alert
Crane --> TelemetryData
IoTDevice --> TelemetryData
IoTHubConnector --> IoTDevice
AIAnalyzer --> TelemetryData
AIAnalyzer --> Alert
NotificationService --> Alert
NotificationService --> User
ReportController --> ReportGenerator
ReportGenerator --> DatabaseManager
DatabaseManager --> TelemetryData
DatabaseManager --> Alert
@enduml
```

---

## Пояснення основних класів

| Клас                                                        | Призначення                                  | Основні методи                                         |
| ----------------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------ |
| **Crane**                                                   | Представляє кран на будмайданчику.           | `isOverloaded()` — визначає, чи перевищено ліміт.      |
| **IoTDevice**                                               | Модель сенсора, що передає дані в систему.   | `sendTelemetry()`, `reconnect()`.                      |
| **TelemetryData**                                           | Телеметрія (вага, час, стан).                | зберігається у БД.                                     |
| **AIAnalyzer**                                              | Модуль машинного навчання для оцінки ризику. | `analyze()`, `predictOverload()`.                      |
| **Alert**                                                   | Оповіщення про критичний стан.               | `notifyUser()` — відправляє через NotificationService. |
| **NotificationService**                                     | Відправка email, push-сповіщень.             | `sendEmail()`, `sendDashboardAlert()`.                 |
| **DatabaseManager**                                         | Доступ до сховища даних (SQL, Blob).         | `saveTelemetry()`, `getCraneHistory()`.                |
| **IoTHubConnector**                                         | Комунікація з Azure IoT Hub.                 | `receiveData()`, `sendCommand()`.                      |
| **ReportGenerator**                                         | Формує звіти для Project Manager.            | `generateSummary()`, `calculateAIMetrics()`.           |
| **DashboardController / ReportController / UserController** | Контролери UI-рівня (MVC).                   | відображення та взаємодія з користувачами.             |

---

## Відповідність принципам SOLID

| Принцип                       | Реалізація в проєкті                                                                                                                                      |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **S — Single Responsibility** | Кожен клас відповідає лише за одну частину логіки: `Crane` — модель об’єкта, `AIAnalyzer` — лише аналіз даних, `NotificationService` — тільки сповіщення. |
| **O — Open/Closed**           | Нові типи сповіщень чи AI-алгоритмів можна додавати, не змінюючи існуючі класи.                                                                           |
| **L — Liskov Substitution**   | Можна розширювати класи `NotificationService` або `DatabaseManager`, не порушуючи функціональності.                                                       |
| **I — Interface Segregation** | Взаємодія між шарами через окремі інтерфейси (`IAnalyzer`, `IRepository`, `INotifier` — потенційно для розширення).                                       |
| **D — Dependency Inversion**  | Контролери не створюють екземпляри напряму — вони отримують сервіси (`AIAnalyzer`, `DatabaseManager`) через ін’єкцію залежностей (DI).                    |

---

## Логічне групування компонентів

```
- Entities (User, Crane, Alert, TelemetryData)
- Services (AIAnalyzer, NotificationService, ReportGenerator)
- Data Access (DatabaseManager, IoTHubConnector)
- Presentation Controllers (DashboardController, UserController, ReportController)
```
