# Горизонтальні прототипи інтерфейсу системи (PlantUML)

---

## Прототип 1 — Головна панель моніторингу (Dashboard)

**Опис:**
Інженер з техніки безпеки бачить список кранів, поточне навантаження, статуси IoT-зв’язку та ризики від AI.

```plantuml
@startuml
title Dashboard – Моніторинг кранів

rectangle "Header" {
  label "AI Crane Monitoring System"
  label "User: Safety Engineer | Logout"
}

rectangle "Sidebar" {
  label "🏠 Dashboard"
  label "📊 Reports"
  label "⚙ Settings"
  label "👥 Users"
}

rectangle "Main Area" {
  label "Crane Status Overview"
  
  rectangle "Crane #1" {
    label "Load: 82% | Status: NORMAL"
  }
  rectangle "Crane #2" {
    label "Load: 96% | Status: WARNING ⚠"
  }
  rectangle "Crane #3" {
    label "Load: 105% | Status: CRITICAL ❗"
  }
}

rectangle "Footer" {
  label "Last updated: 12:01:25 | Data refresh every 5s"
}

@enduml
```

---

## Прототип 2 — Вікно сповіщень (Alerts & Notifications)

**Опис:**
Оператор крана або інженер отримує візуальні сповіщення про перевантаження та може підтвердити, що ознайомився з ними.

```plantuml
@startuml
title Alerts – Критичні повідомлення

rectangle "Header" {
  label "ALERT CENTER"
  label "Active Alerts | Acknowledged | History"
}

rectangle "Alert List" {
  rectangle "Alert #1" {
    label "Crane #3 – Critical overload (105%)"
    label "Time: 12:01:10"
    label "Status: UNRESOLVED"
    label "Actions: [Acknowledge] [View Details]"
  }
  rectangle "Alert #2" {
    label "Crane #2 – Warning (96%)"
    label "Time: 11:54:33"
    label "Status: Acknowledged"
  }
}

rectangle "Alert Details" {
  label "Selected Alert: Crane #3"
  label "AI Risk Score: 0.95"
  label "Recommended Action: Stop lift immediately."
}

@enduml
```

---

## Прототип 3 — Сторінка звітів і аналітики (Reports)

**Опис:**
Керівник проєкту формує звіт про інциденти, бачить графіки безпеки та метрики точності AI.

```plantuml
@startuml
title Reports – Аналітика безпеки

rectangle "Header" {
  label "Reports and Analytics"
  label "Period: [Last 7 days ▼]   [Generate PDF]"
}

rectangle "Report Summary" {
  label "Total Alerts: 58"
  label "Critical: 5 | Warning: 12 | Normal: 41"
}

rectangle "Charts" {
  rectangle "Incident Trend" {
    label "📈 Risk events over time"
  }
  rectangle "AI Accuracy" {
    label "Model Accuracy: 96.2%"
  }
  rectangle "Average Reaction Time" {
    label "Mean reaction time: 3.8s"
  }
}

@enduml
```

---

## Прототип 4 — Керування користувачами (User Management)

**Опис:**
Адміністратор додає користувачів, задає ролі доступу, блокує чи активує облікові записи.

```plantuml
@startuml
title User Management – Адміністрування користувачів

rectangle "Header" {
  label "User Management Panel"
  label "Admin: System Administrator"
}

rectangle "User Table" {
  label "ID | Name | Role | Status | Actions"
  label "U001 | Ivan Petrenko | Operator | Active | [Edit] [Block]"
  label "U002 | Oksana Lebid | Safety Engineer | Active | [Edit] [Block]"
  label "U003 | Mykola Kovalenko | Project Manager | Inactive | [Activate]"
}

rectangle "Add User Form" {
  label "Add New User:"
  label "Name: [_________]"
  label "Email: [_________]"
  label "Role: [Operator ▼]"
  label "[Create User]"
}

@enduml
```

---

## Прототип 5 — Налаштування IoT-пристроїв (IoT Settings)

**Опис:**
Адміністратор може підключати або відключати сенсори, перевіряти статус зв’язку з Azure IoT Hub.

```plantuml
@startuml
title IoT Device Settings – Налаштування IoT-пристроїв

rectangle "Header" {
  label "IoT Devices | Connection status | Sync"
}

rectangle "Device List" {
  rectangle "Device #1" {
    label "ID: CRANE_SENSOR_001"
    label "Status: Connected ✅"
    label "Last Sync: 12:02:10"
  }
  rectangle "Device #2" {
    label "ID: CRANE_SENSOR_002"
    label "Status: Disconnected ❌"
    label "Last Sync: 11:59:30"
  }
}

rectangle "Controls" {
  label "[+ Add New Device]"
  label "[Test Connection]"
  label "[Refresh All]"
}

@enduml
```