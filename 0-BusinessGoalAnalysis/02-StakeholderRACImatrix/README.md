## RACI матриця.

| Завдання                                         | Responsible (R)    | Accountable (A)  | Consulted (C)                               | Informed (I)                    |
| ------------------------------------------------ | ------------------ | ---------------- | ------------------------------------------- | ------------------------------- |
| Визначення бізнес-цілей та критеріїв успіху      | Business Analyst   | Product Owner    | CEO (спонсор проекту), Safety Experts       | DevTeam, QA Engineer            |
| Збір (виявлення) бізнес-вимог, обмежень, ризиків | Business Analyst   | Product Owner    | PM, System Architect, Safety Experts        | DevTeam, QA Engineer            |
| Збір вимог користувачів                          | Business Analyst   | Product Owner    | End Users, Safety Experts                   | DevTeam, QA Engineer            |
| Аналіз вимог                                     | Business Analyst   | System Architect | PM, Product Owner                           | DevTeam                         |
| Специфікація (документація) вимог                | Business Analyst   | PM               | System Architect, Product Owner             | DevTeam                         |
| Проектування архітектури системи                 | System Architect   | PM               | IoT Engineer, ML Engineer                   | Business Analyst, Product Owner |
| Розробка системи                                 | DevTeam            | PM               | System Architect, ML Engineer, IoT Engineer | QA Engineer, Product Owner      |
| Розробка та тренування ML-моделей                | ML Engineer        | System Architect | IoT Engineer, Business Analyst              | DevTeam, QA Engineer            |
| Інтеграція IoT-сенсорів та каналів збору даних   | IoT Engineer       | System Architect | ML Engineer, DevTeam                        | QA Engineer                     |
| Тестування системи                               | QA Engineer        | PM               | Product Owner, Business Analyst             | DevTeam                         |
| Перевірка відповідності нормам безпеки           | Safety Experts     | Product Owner    | Regulatory Experts                          | PM                              |
| Перевірка відповідності стандартам регуляторів   | Regulatory Experts | Product Owner    | Safety Experts                              | PM                              |
| Презентація та приймання рішення щодо релізу     | Product Owner      | CEO              | PM, Business Analyst                        | DevTeam, QA Engineer            |
