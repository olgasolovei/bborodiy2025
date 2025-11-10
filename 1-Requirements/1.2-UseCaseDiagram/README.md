@startuml
left to right direction
skinparam actorStyle awesome
skinparam packageStyle rectangle
skinparam usecase {
  BackgroundColor #f9f9f9
  BorderColor #333
  ArrowColor #666
  FontStyle bold
}

actor "Site Safety Engineer" as SafetyEng
actor "Crane Operator" as Operator
actor "Project Manager" as PM
actor "System Administrator" as Admin
actor "AI Monitoring Service" as AIMonitor
actor "IoT Device" as IoT

rectangle "AI-powered Construction Site Monitoring System" {
  
  (Перегляд поточного стану кранів) as UC01
  (Реагування на критичне попередження) as UC02
  (Отримання попередження про перевантаження) as UC03
  (Перевірка журналу подій) as UC04
  (Формування звіту про безпеку) as UC05
  (Аналіз ефективності системи AI) as UC06
  (Реєстрація нового користувача) as UC07
  (Підключення нового IoT-пристрою) as UC08
  (Аналіз телеметрії кранів) as UC09

  SafetyEng -- UC01
  SafetyEng -- UC02
  Operator -- UC03
  Operator -- UC04
  PM -- UC05
  PM -- UC06
  Admin -- UC07
  Admin -- UC08
  AIMonitor -- UC09
  AIMonitor -- UC02
  AIMonitor -- UC03
  IoT -- UC09

  UC02 .> UC01 : «include»
  UC03 .> UC09 : «include»
  UC05 .> UC04 : «include»
  UC06 .> UC05 : «extend»
}

@enduml

