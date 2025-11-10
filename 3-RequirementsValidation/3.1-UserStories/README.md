# Користувацькі історії (User Stories) з критеріями приймального тестування

---

## Епік 1 — Моніторинг кранів у реальному часі

**User Story 1.1**

> Як **інженер з техніки безпеки**,
> я хочу **переглядати дані про поточне навантаження на кожен кран у реальному часі**,
> щоб **вчасно реагувати на перевищення допустимих значень і запобігати аваріям.**

### Acceptance Criteria (Gherkin)

```gherkin
Feature: Real-time crane load monitoring

  Scenario: Display crane load data on dashboard
    Given the system is connected to IoT sensors
    When the Safety Engineer opens the monitoring dashboard
    Then the dashboard must display current load, crane ID, and status ("Normal", "Warning", or "Critical")

  Scenario: Update data in real time
    Given IoT data stream is active
    When new load data arrives
    Then the dashboard updates within 5 seconds without manual refresh
```

---

## Епік 2 — Автоматичне виявлення ризиків перевантаження

**User Story 2.1**

> Як **AI-модуль системи**,
> я хочу **аналізувати показники навантаження**,
> щоб **визначати перевищення допустимої межі та створювати автоматичні попередження.**

### Acceptance Criteria (Gherkin)

```gherkin
Feature: Automatic overload detection

  Scenario: Detect overload condition
    Given the crane load exceeds the configured safe limit
    When the AI module processes incoming data
    Then the system must generate a "Critical Overload" alert

  Scenario: Categorize risk level
    Given current load is within 80–100% of the limit
    When AI evaluates data
    Then it classifies risk as "Warning"
```

---

## Епік 3 — Сповіщення користувачів про небезпечні ситуації

**User Story 3.1**

> Як **оператор крана**,
> я хочу **отримувати миттєве візуальне або звукове сповіщення**,
> щоб **негайно зупинити операцію у разі перевантаження.**

### Acceptance Criteria (Gherkin)

```gherkin
Feature: Real-time operator alerts

  Scenario: Visual and sound alert
    Given crane load reaches 100% of the limit
    When overload is detected
    Then the operator interface displays a red warning and plays an alarm sound

  Scenario: Email notification to Safety Engineer
    Given an overload event occurs
    When the AI system generates a critical alert
    Then the system sends an email to the Safety Engineer within 5 seconds
```

---

## Епік 4 — Управління користувачами та ролями доступу

**User Story 4.1**

> Як **системний адміністратор**,
> я хочу **створювати нових користувачів і призначати ролі**,
> щоб **контролювати рівень доступу до функцій системи.**

### Acceptance Criteria (Gherkin)

```gherkin
Feature: User management and role control

  Scenario: Add a new user
    Given the admin is logged into the system
    When the admin creates a new user with the role "Operator"
    Then the user receives login credentials via email

  Scenario: Access restriction by role
    Given the user is logged in as "Operator"
    When they try to access admin configuration
    Then access is denied with a "Permission denied" message
```

---

## Епік 5 — Аналітика і звітність

**User Story 5.1**

> Як **керівник проєкту**,
> я хочу **отримувати щотижневі звіти про ризики і кількість інцидентів**,
> щоб **оцінювати ефективність системи і роботу AI-моделі.**

### Acceptance Criteria (Gherkin)

```gherkin
Feature: Safety reports and analytics

  Scenario: Generate safety report
    Given a Project Manager requests a report for the last 7 days
    When the system aggregates event logs and AI performance data
    Then a PDF report is generated within 10 seconds

  Scenario: Display AI accuracy metrics
    Given the system has processed incidents for a month
    When the manager opens the analytics dashboard
    Then the dashboard shows model accuracy ≥ 95%
```

---

## Епік 6 — Протоколювання подій

**User Story 6.1**

> Як **QA-інженер**,
> я хочу **переглядати журнал усіх подій і сповіщень**,
> щоб **переконатись, що система фіксує кожну дію користувача та AI.**

### Acceptance Criteria (Gherkin)

```gherkin
Feature: Event logging

  Scenario: Log user actions
    Given a user logs into the system
    When they perform any action (e.g., acknowledge alert)
    Then the system records the username, action, and timestamp

  Scenario: Log AI alerts
    Given an AI alert is generated
    When the event occurs
    Then it is recorded in the log with status and severity level
```

---

## Епік 7 — Надійність і стабільність роботи

**User Story 7.1**

> Як **системний архітектор**,
> я хочу **щоб система продовжувала роботу навіть при втраті зв’язку з одним IoT-пристроєм**,
> щоб **забезпечити стійкість та безперервність моніторингу.**

### Acceptance Criteria (Gherkin)

```gherkin
Feature: System reliability

  Scenario: Auto reconnection on IoT failure
    Given one IoT sensor disconnects
    When connection is restored
    Then the system resumes data reception within 10 seconds

  Scenario: Data integrity check
    Given data packets arrive after reconnection
    When AI processes delayed telemetry
    Then missing data points are marked as "recovered"
```