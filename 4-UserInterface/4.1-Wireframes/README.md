# Проєкт каркасу інтерфейсу користувача (Wireframes)

Мета: показати, **як різні ролі системи (інженер з ТБ, оператор, менеджер, адміністратор)** взаємодіють з веб-додатком моніторингу будівельних майданчиків, який виявляє ризик **перекидання крана через перевантаження**.

---

## 1. Wireframe: Екран входу (Login)

Це потрібно, бо в попередніх лабораторних ми ввели ролі (FR6: керування користувачами).

```plantuml
@startuml
salt
{
  {+
    Login to AI Crane Monitoring
  }
  {
    Username | [__________________]
    Password | [__________________]
  }
  {
    [ Login ]
    [ Forgot password ]
  }
  {
    tip: "Access restricted to authorized site staff"
  }
}
@enduml
```

---

## 2. Wireframe: Dashboard (моніторинг у реальному часі)

Це головний екран, який реалізує FR1, FR2, FR3, FR7 і наші User Stories з ЛР4 (US1.1, US2.1, US3.1).

```plantuml
@startuml
salt
{
  {+
    Dashboard – Real-time crane monitoring
  }
  { 
    Menu:
    [Dashboard] 
    [Alerts] 
    [Reports] 
    [IoT Devices] 
    [Users] 
    [Logout]
  }
  {
    == Crane status ==
    "Crane #1" | "Load: 82%" | "Status: NORMAL"
    "Crane #2" | "Load: 96%" | "Status: WARNING"
    "Crane #3" | "Load: 105%" | "Status: CRITICAL"
  }
  {
    == Live feed ==
    Last update: 12:01:25
    Refresh: 5 sec
  }
  {
    == Quick actions ==
    [View Alerts]
    [View Logs]
  }
}
@enduml
```

Тут ми явно показали:

* оновлення в реальному часі (NFR7),
* різні статуси (зелений/жовтий/червоний із NFR18),
* навігацію на Alerts.

---

## 3. Wireframe: Alerts (центр сповіщень)

Цей екран напряму відповідає FR7 і US3.1 (оператор отримує миттєве сповіщення).

```plantuml
@startuml
salt
{
  {+
    Alerts – Active and historical alerts
  }
  {
    [← Back to Dashboard]
  }
  {
    == Active alerts ==
    "12:01:10" | "Crane #3" | "CRITICAL overload (105%)" | [Acknowledge]
    "11:54:33" | "Crane #2" | "WARNING (96%)" | [Acknowledge]
  }
  {
    == Alert details ==
    Crane: Crane #3
    AI risk score: 0.95
    Recommended action: Stop lifting immediately
    Notified: Safety Engineer (email)
  }
}
@enduml
```

---

## 4. Wireframe: Reports (аналітика та звіти)

Це з ЛР2 (Use Case UC-05, UC-06) і з FR5/NFR12 з ЛР3.

```plantuml
@startuml
salt
{
  {+
    Reports – Safety and AI analytics
  }
  {
    Period: [ Last 7 days ▼ ]
    [ Generate PDF ]
  }
  {
    == Summary ==
    Total alerts: 58
    Critical: 5
    Warnings: 12
  }
  {
    == Charts (placeholder) ==
    [ Incidents over time ]
    [ AI accuracy: 96% ]
  }
}
@enduml
```

---

## 5. Wireframe: User Management (для Admin)

Це реалізація FR6 (керування користувачами та ролями) з ЛР3 і нашого UC-07 з ЛР2.

```plantuml
@startuml
salt
{
  {+
    User Management
  }
  {
    [Add user]
  }
  {
    "User" | "Role" | "Status" | ""
    "safety.eng@site" | "Safety Engineer" | "Active" | [Edit]
    "crane.op@site"   | "Operator"        | "Active" | [Edit]
    "pm@site"         | "Project Manager" | "Active" | [Edit]
    "admin@site"      | "Admin"           | "Active" | [Edit]
  }
  {
    == Add new user ==
    Name: [___________]
    Email: [___________]
    Role: [Operator ▼]
    [Create]
  }
}
@enduml
```

---

## 6. Wireframe: IoT Devices (підключення сенсорів)

Це те, що ми вже вводили в ЛР2 (UC-08) і що вимагається завданням (бо система працює з Azure IoT Hub).

```plantuml
@startuml
salt
{
  {+
    IoT Devices – Connected sensors
  }
  {
    [Add device] [Test connection] [Refresh]
  }
  {
    "Device ID" | "Crane" | "Status" | "Last sync"
    "CRANE_SENSOR_001" | "Crane #1" | "Connected ✅" | "12:02:10"
    "CRANE_SENSOR_002" | "Crane #2" | "Disconnected ❌" | "11:59:30"
  }
  {
    == Device details ==
    Connection: Azure IoT Hub
    Telemetry: enabled
  }
}
@enduml
```