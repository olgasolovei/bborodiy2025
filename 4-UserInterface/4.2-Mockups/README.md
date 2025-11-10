# Проєкт макетів інтерфейсу користувача (Mockups)

---

## **NFR_7 – Простота експлуатації (Usability)**

**Екран:** Dashboard
**Принцип:** мінімалізм, зручність, зосередження на ключовій інформації.

```plantuml
@startuml
skinparam titleBorderRoundCorner 15
skinparam titleBorderThickness 2
skinparam titleBorderColor #0066CC

title NFR_7 – Панель моніторингу (Простота експлуатації)

package "Dashboard" #E6F2FF {
  rectangle "AI Crane Monitoring System" as header #0066CC
  frame "Меню навігації" {
    rectangle "🏠 Dashboard" #CCE5FF
    rectangle "📊 Reports" #CCE5FF
    rectangle "⚠ Alerts" #CCE5FF
    rectangle "🔧 IoT Devices" #CCE5FF
    rectangle "👥 Users" #CCE5FF
  }

  frame "Стан кранів" {
    rectangle "Crane #1 – 82% load | NORMAL ✅" #CCFFCC
    rectangle "Crane #2 – 96% load | WARNING ⚠" #FFF5CC
    rectangle "Crane #3 – 105% load | CRITICAL ❌" #FFCCCC
  }

  frame "Інформація" {
    rectangle "Оновлення: кожні 5 секунд" #E6F2FF
    rectangle "Підключення: Azure IoT Hub ✅" #E6F2FF
  }
}
@enduml
```

---

## **NFR_9 – Візуальне виділення критичних станів**

**Екран:** Alerts
**Принцип:** миттєве розпізнавання небезпеки.

```plantuml
@startuml
skinparam titleBorderRoundCorner 15
skinparam titleBorderColor #CC0000

title NFR_9 – Центр сповіщень (Виділення критичних станів)

package "Alerts Center" #FFE6E6 {
  rectangle "🚨 CRITICAL: Crane #3 перевантаження 105%" #CC0000
  rectangle "⚠ WARNING: Crane #2 навантаження 96%" #FFCC00
  rectangle "ℹ INFO: Crane #1 стабільна робота" #99CC99
}

package "Дії користувача" #FFF5F5 {
  rectangle "[Acknowledge Alert]" #CC0000
  rectangle "[View Details]" #666666
}
@enduml
```

---

## **NFR_12 – Продуктивність системи**

**Екран:** Reports
**Принцип:** швидке завантаження, чіткі графіки, мінімум відволікань.

```plantuml
@startuml
skinparam titleBorderRoundCorner 15
skinparam titleBorderColor #0099CC

title NFR_12 – Аналітика безпеки (Продуктивність)

package "Reports and Analytics" #E6FFFF {
  rectangle "Період: [Last 7 days ▼]" #CCFFFF
  rectangle "[Generate PDF]" #0099CC

  frame "Підсумок" {
    rectangle "Total Alerts: 58 | Critical: 5 | Warning: 12" #E6FFFF
  }

  frame "AI Performance" {
    rectangle "📈 Risk over time" #E6F2FF
    rectangle "Model Accuracy: 96.2%" #CCFFCC
    rectangle "Avg Reaction Time: 3.8s" #FFFFCC
  }

  rectangle "Report generated in 8.5s ✅" #E6FFFF
}
@enduml
```

---

## **NFR_13 – Безпека користувачів і доступу (Security)**

**Екран:** User Management
**Принцип:** чітка рольова структура, шифрування, контроль прав.

```plantuml
@startuml
skinparam titleBorderRoundCorner 15
skinparam titleBorderColor #990099

title NFR_13 – Керування користувачами (Безпека)

package "User Management" #F9E6FF {
  frame "Список користувачів" {
    rectangle "SafetyEngineer@site | Safety Engineer | Active" #E6CCFF
    rectangle "CraneOp@site | Operator | Active" #E6CCFF
    rectangle "Admin@site | Administrator | Active" #E6CCFF
  }

  frame "Новий користувач" {
    rectangle "Name: [_________]" #FFFFFF
    rectangle "Email: [_________]" #FFFFFF
    rectangle "Role: [Operator ▼]" #FFFFFF
    rectangle "[Create User]" #990099
  }

  frame "Security Info" {
    rectangle "Паролі зберігаються за алгоритмом bcrypt" #F9E6FF
    rectangle "RBAC контроль доступів" #F9E6FF
  }
}
@enduml
```

---

## **NFR_15 – Надійність системи (Availability ≥ 99.5%)**

**Екран:** IoT Devices
**Принцип:** моніторинг доступності, статуси підключень, швидке відновлення.

```plantuml
@startuml
skinparam titleBorderRoundCorner 15
skinparam titleBorderColor #006600

title NFR_15 – IoT Devices (Надійність)

package "IoT Connections" #E6FFE6 {
  rectangle "Device ID | Crane | Status | Last Sync" #CCFFCC
  rectangle "CRANE_SENSOR_001 | Crane #1 | Connected ✅ | 12:02:10" #99FF99
  rectangle "CRANE_SENSOR_002 | Crane #2 | Disconnected ❌ | 11:59:30" #FFCCCC
}

package "Дії" #E6FFE6 {
  rectangle "[+ Add Device]" #006600
  rectangle "[Test Connection]" #009900
  rectangle "[Reconnect All]" #006600
}

rectangle "System Uptime: 99.8% | Auto-reconnect Enabled" #E6FFE6
@enduml
```

---

## **NFR_17 – Інтуїтивне налаштування порогів сповіщення (Ease of configuration)**

**Екран:** Alert Settings
**Принцип:** інтуїтивність, простота введення, кольорова індикація рівнів ризику.

```plantuml
@startuml
skinparam titleBorderRoundCorner 15
skinparam titleBorderColor #FF9900

title NFR_17 – Пороги сповіщень (Інтуїтивне налаштування)

package "Alert Threshold Settings" #FFF2CC {
  rectangle "Low risk threshold: [80% ▼]" #FFFFCC
  rectangle "High risk threshold: [100% ▼]" #FFCC99
  rectangle "Notification delay: [3s ▼]" #FFF5CC
  rectangle "[Save Changes]" #FF9900
}

package "Help and Tips" #FFF2CC {
  rectangle "Рекомендовані значення: Warning – 80%, Critical – 100%" #FFF9E6
}
@enduml
```

---

## Підсумкова таблиця

| Макет                  | NFR | Екран          | Основний принцип           | Колірна тема               |
| ---------------------- | --- | -------------- | -------------------------- | -------------------------- |
| NFR_7_Dashboard        | 7   | Dashboard      | Простота, зрозумілість     | Блакитна (успокійлива)     |
| NFR_9_Alerts           | 9   | Alerts         | Виділення ризиків          | Червона (тривога)          |
| NFR_12_Reports         | 12  | Reports        | Продуктивність, швидкість  | Бірюзова (аналітика)       |
| NFR_13_UserManagement  | 13  | Users          | Безпека, контроль доступів | Фіолетова (авторитетність) |
| NFR_15_IoTDevices      | 15  | IoT Devices    | Надійність, стабільність   | Зелена (стійкість)         |
| NFR_17_AlertThresholds | 17  | Alert Settings | Інтуїтивність, простота    | Помаранчева (налаштування) |

---