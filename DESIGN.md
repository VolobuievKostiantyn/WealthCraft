# 🛠️ WealthCraft – Software Design Description

## 📌 Overview

**WealthCraft** is an open-source Android game that teaches personal finance through interactive simulation. Players manage income, expenses, assets, and liabilities to reach financial independence.

The game is built in **Kotlin**, using **Jetpack Compose**, and follows **MVVM architecture** with a modular structure and local persistence via Room.

---

## ⚙️ Architecture Overview

Presentation Layer └── UI (Jetpack Compose) └── Screens, Components, Navigation

ViewModel Layer └── ViewModels (State management via StateFlow)

Domain Layer └── UseCases (Business logic)

Data Layer ├── Repository Interface ├── Repository Implementation ├── Room Database (DAO, Entities) └── Mappers (DTO ↔ Domain)

DI Layer └── Hilt Modules

## 🧩 Core Modules

### Player Profile
Represents the user’s chosen profession, salary, taxes, and starting expenses. Editable at game start and customizable by the player.

### Entities Engine
Modular system to define and manage **Jobs**, **Assets**, **Liabilities**, **Events**, and **Opportunities**.  
Players can add, edit, or delete custom entities (stored locally using JSON or Room).

### Game State Engine
Tracks financial metrics: **income**, **expenses**, **cash flow**, **net worth**, **passive income**.  
Provides logic for achieving the win condition (financial independence).

### Turn System
Each round represents a unit of time (e.g., a month). Players make decisions, experience events, and process recurring cash flow.

### Event Engine
Supports both **random** and **scripted** events (e.g., layoff, market boom). Events affect the player’s metrics and strategy.

### Persistence Layer
- Room Database for storing entities and game progress
- Supports **autosave**, **manual save**, and **import/export** (e.g., JSON backup)

---

## 🔧 Tech Stack

| Component            | Technology              |
|----------------------|--------------------------|
| Language             | Kotlin                   |
| UI Framework         | Jetpack Compose          |
| Architecture         | MVVM                     |
| State Management     | ViewModel + StateFlow    |
| Dependency Injection | Hilt                     |
| Database             | Room                     |
| Testing              | JUnit, AndroidX Test     |
| Build System         | Gradle (KTS)             |

---

## 🌟 Unique Feature: Dynamic Sandbox Economy

WealthCraft allows players to **create, modify, or remove** in-game entities such as jobs, investments, expenses, and events. This supports:

- Custom financial simulations
- Personalized or real-life scenarios
- Scenario sharing and experimentation

Example custom asset in JSON:
```json
{
  "type": "asset",
  "name": "Rental Property",
  "cost": 10000,
  "monthly_income": 500,
  "risk": "low"
}


---

🧪 Testing Strategy

Unit Tests: Financial calculations, event resolution, win conditions

UI Tests: Screen flows, interactions

Data Tests: Entity JSON validation, Room DB integrity

State Tests: Cash flow and balance sheet consistency

🚀 Roadmap / Planned Features

[ ] Onboarding tutorial for new players

[ ] Player-defined goals and achievements

[ ] Exportable financial reports (CSV/PDF)

[ ] Peer-to-peer scenario sharing

[ ] Offline AI assistant for financial advice
