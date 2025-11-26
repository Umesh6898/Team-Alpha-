# 🏔️ Himachal Pradesh Air Quality Dashboard

A lightweight, real-time Air Quality Index (AQI) dashboard built with vanilla JavaScript and Tailwind CSS, providing current data, health advisories, and an AI-powered summary for major locations in Himachal Pradesh, India.

## ✨ Features

* **12-District Coverage:** Provides Air Quality data for key locations across all 12 districts of Himachal Pradesh (Mock Data).
* **AQI Visualization:** Displays the current AQI with a color-coded status (Good, Moderate, Unhealthy for Sensitive Groups, etc.).
* **Pollutant Breakdown:** Detailed view of key pollutants (PM2.5, PM10, Ozone, NO2, CO, SO2) concentrations.
* **Tailored Health Advisory:** Provides specific advice for the general public, sensitive groups, and individuals with respiratory conditions based on the current AQI.
* **Gemini AI Summary:** Integrates the **Gemini API** (specifically `gemini-2.5-flash`) to generate a concise, hyper-local, and expert interpretation of the current air quality situation and recommended actions.
* **Responsive Design:** Built using Tailwind CSS for a seamless experience on both mobile and desktop.

## 🚀 Setup and Installation

This project is a single-page application and does not require a build step.

### Prerequisites

1.  **A Gemini API Key:** You will need an API key to enable the AI Health Summary feature. You can get one from Google AI Studio.

### Steps

1.  **Save the Code:** Save the provided HTML code into a file named `index.html`.
2.  **Open the File:** Open `index.html` directly in your web browser.
3.  **Enable the API Key:**
    * Find the following line in the `<script>` tag:
        ```javascript
        appState.apiKey = ""; // Automatically handled by Canvas
        ```
    * Replace the empty string with your actual Gemini API Key:
        ```javascript
        appState.apiKey = "YOUR_GEMINI_API_KEY_HERE";
        ```
4.  The dashboard will load with the default location. Use the dropdown in the top right corner to select a different location.

## 📊 Data Source

The air quality data is currently powered by **mock data** (`MOCK_HP_DATA` in the JavaScript). This allows the dashboard's features and the AI summary generation to be demonstrated without relying on a live external API.

The data structure includes:
* `aqi`: Current Air Quality Index.
* `dominant`: The main pollutant contributing to the AQI.
* `health`: A general health message.
* `pollutantData`: Detailed values for individual pollutants (PM2.5, Ozone, NO2, PM10, CO, SO2).

## 🧠 AI Integration

The dashboard uses the Gemini API to provide an on-demand, contextualized summary of the air quality.

### Model and Prompt

* **Model:** `gemini-2.5-flash`
* **Goal:** To interpret the raw AQI data into actionable, local health advice.
* **System Instruction:**
    > "Act as a friendly, reliable, and hyper-local air quality specialist for HP. Keep the summary concise (max 3 sentences) and the tone supportive."
* **User Query:** A detailed prompt is constructed with the current location, AQI, category, and dominant pollutant, asking the AI to focus on immediate health implications considering the unique mountainous environment of Himachal Pradesh.

### Functionality

The `generateLlmSummary(data)` function automatically calls the Gemini API after the AQI data is fetched. Users can also manually regenerate the summary by clicking the **bell icon** in the header.

## 🛠️ Technology Stack

* **HTML5:** Structure of the dashboard.
* **Vanilla JavaScript:** Logic, state management, data fetching, and DOM manipulation.
* **Tailwind CSS (CDN):** Styling and utility-first design framework.
