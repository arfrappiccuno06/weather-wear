# WeatherWear

A Java-based outfit recommendation application that provides personalized clothing suggestions based on real-time weather conditions, location, and individual style preferences.

> **Note:** This was a collaborative team project developed at the University of Toronto for CSC207 (Software Design). I was primarily responsible for **Use Case 3: Personalized Style Recommendation**, implementing the AI-powered outfit generation feature with full Clean Architecture compliance and 100% test coverage.

## Features

- **Real-time Weather Forecasting** – Displays hourly weather conditions including temperature, precipitation, wind speed, and UV index
- **AI-Powered Outfit Generation** – Creates personalized outfit suggestions using Google Gemini API based on weather conditions and user preferences
- **User Profile Management** – Saves style preferences (casual, formal, sporty), gender, and favorite colors for tailored recommendations
- **Multiple Suggestion Variations** – Generates alternative outfit options if the initial suggestion doesn't match user preferences
- **Accessory Recommendations** – Suggests weather-appropriate accessories (umbrella, sunglasses, etc.) based on outing purpose
- **Location-Based Services** – Automatically detects user location or allows manual city input

## Tech Stack

- **Language:** Java 11
- **GUI Framework:** Java Swing
- **Build Tool:** Maven
- **Architecture:** Clean Architecture with strict layer separation
- **Testing:** JUnit (100% coverage on use case interactors)

### APIs & External Services
- **OpenWeatherMap API** – Real-time and forecasted weather data
- **Google Gemini AI API** – Natural language processing for outfit generation
- **Supabase** – Backend storage for user profiles and preferences

### Libraries
- **OkHttp** (v4.11.0) – HTTP client for API calls
- **org.json** (v20240303) – JSON parsing and manipulation

## How It Works

1. **Location Detection** – User grants location access or manually enters their city
2. **Weather Retrieval** – App fetches current conditions and hourly forecast via OpenWeatherMap API
3. **AI Processing** – Weather data + user style preferences are sent to Google Gemini API
4. **Outfit Generation** – AI generates detailed outfit suggestions including:
    - Clothing items (tops, bottoms, outerwear)
    - Color recommendations
    - Fabric suggestions
    - Accessories based on weather conditions
5. **Display & Iteration** – User views suggestions and can request alternative options

## Architecture

This project strictly follows **Clean Architecture** principles with clear separation of concerns:
```
src/main/java/
├── entity/              # Business entities (User, Weather, DailyForecast)
├── use_case/            # Business logic interactors
│   ├── outfit_suggestion/
│   └── ...
├── interface_adapter/   # Controllers, Presenters, ViewModels
│   ├── outfit_suggestion/
│   └── ...
├── view/                # Swing GUI components
└── data_access/         # API gateways and DAOs
```

**Key Design Patterns:**
- Dependency Inversion (all dependencies point inward)
- Interface Segregation (separate input/output boundaries)
- Single Responsibility (each class has one job)
- Strategy Pattern (interchangeable data access implementations)

## Use Cases Implemented

| Use Case | Lead Developer | Description |
|----------|---------------|-------------|
| View Daily Weather Forecast | Steven | Displays hourly weather data with temperature, precipitation, and wind speed |
| Generate Weather-Based Outfit | Jason | Creates basic outfit suggestions based on current weather |
| **Personalized Style Recommendation** | **Arfa (me)** | **AI-powered personalized outfits matching user style preferences** |
| Manage User Profile | Amey | User authentication and profile data persistence |
| Request Additional Suggestions | Bhavikaa | Generate alternative outfit variations |
| Accessory Recommendations | Vicky | Suggests accessories based on weather and outing purpose |

## Testing

All use case interactors have **100% code coverage** using JUnit. Tests include:
- Mock objects for external API calls (no actual API requests during testing)
- Success and failure scenarios
- Edge cases and boundary conditions
- Integration tests for end-to-end functionality

Example test coverage for `OutfitSuggestionInteractor`:
```java
- testSuccessfulOutfitGeneration()
- testAPIFailureHandling()
- testInvalidUserPreferences()
- testEmptyWeatherData()
```

## Team

**Team Twelve** – University of Toronto (Fall 2024)
- Steven (Weather Forecasting)
- Jason (Basic Outfit Generation)
- **Arfa** (Personalized AI Recommendations) ← *My contribution*
- Amey (User Authentication & Profiles)
- Bhavikaa (Additional Suggestions)
- Vicky (Accessory Recommendations)

## My Contributions

### Primary Responsibility: Use Case 3 – Personalized Style Recommendation
**Files Created (13 total across all layers):**
- `OutfitSuggestionInteractor.java` – Core business logic
- `OutfitSuggestionDataAccessObject.java` – Google Gemini API integration
- `OutfitSuggestionController.java` – Interface adapter
- `OutfitSuggestionPresenter.java` – Output formatting
- `OutfitSuggestionView.java` – Swing GUI panel
- Input/Output data structures and boundary interfaces
- Comprehensive unit tests (100% coverage)

**Technical Achievements:**
- Integrated Google Gemini AI API with proper error handling
- Implemented Clean Architecture with zero layer violations
- Created robust testing suite with mock API responses
- Designed intuitive Swing GUI for outfit display

### Code Reviews
- Identified security issue: exposed API keys in teammate's code
- Caught bug: misspelled method name causing runtime errors
- Suggested refactoring: extracted repeated code into helper methods

## Installation & Setup

1. **Clone the repository**
```bash
   git clone https://github.com/[your-username]/WeatherWear.git
   cd WeatherWear
```

2. **Configure API Keys**
    - Get a free API key from [OpenWeatherMap](https://openweathermap.org/api)
    - Get a Google Gemini API key from [Google AI Studio](https://aistudio.google.com/app/api-keys)
    - Create configuration files (details in `src/main/java/data_access/`)

3. **Build with Maven**
```bash
   mvn clean install
```

4. **Run the application**
```bash
   mvn exec:java -Dexec.mainClass="app.Main"
```

## Future Enhancements

- **Web/Mobile Interface** – Convert to React frontend with RESTful API backend
- **Machine Learning** – Train custom model on user feedback to improve recommendations
- **Social Features** – Share outfit suggestions with friends
- **Wardrobe Management** – Track owned clothing items and suggest combinations
- **Multi-day Planning** – Generate outfit plans for entire week

## License

This project was developed for educational purposes as part of CSC207 at the University of Toronto.

## Acknowledgments

- Course instructors and TAs for guidance on Clean Architecture
- Team Twelve for collaborative development
- OpenWeatherMap and Google for providing free API access

---

**Note:** This project demonstrates proficiency in object-oriented design, software architecture patterns, API integration, testing methodologies, and collaborative Git workflows – skills directly applicable to software engineering roles.