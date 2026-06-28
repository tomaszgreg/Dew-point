# Dew Point Calculator with Interactive Chart

A lightweight, high-performance, single-file responsive web application for calculating dew point temperature and analyzing psychrometric trends. The application is built entirely using vanilla HTML, CSS, and JavaScript, leveraging Chart.js for data visualization.

## Features

- **Smart Single Input Parsing:** Accepts temperature and relative humidity directly from a single text field separated by a space (e.g., `21.5 55`). It dynamically supports both dot (`.`) and comma (`,`) decimal separators.
- **Advanced Psychrometric Charting:** Integrates a responsive `Chart.js` scatter plot containing pre-calculated reference curves for standard dew point isotherms ($T_d = 5^\circ\text{C}$ to $25^\circ\text{C}$), computed using the inverted Magnus-Tetensa approximation.
- **Dynamic Visual Hierarchy:**
  - **Green:** Represents the latest real-time calculation.
  - **Blue:** Displays the historical trend points.
  - **Yellow:** Highlights a specific historical point when clicked on the UI list.
- **Persistent State Tracking:** Automatic synchronization with the browser's `localStorage` ensuring configuration preferences (such as selected language) and calculation datasets persist across page reloads and sessions.
- **Granular Dataset Management:** Provides native controls to remove single individual anomalies or calculations from the history via an inline deletion control ($	imes$), or completely wipe the registry with a master reset option.
- **Full Localization (i18n):** Supports seamless runtime switching between **English (EN)** and **Polish (PL)** across all interfaces, errors, chart axes, tooltips, and presets.
- **Sleek Engineering UI:** Tailored with a modern, low-fatigue dark mode palette inspired by industrial monitoring dashboards.

## Mathematical Formulation

The app relies on the globally standardized **Magnus-Tetensa equation** to determine the dew point temperature ($T_d$) from ambient temperature ($T$) and relative humidity ($RH$):

$$\alpha(T, RH) = \frac{a \cdot T}{b + T} + \ln\left(\frac{RH}{100}\right)$$

$$T_d = \frac{b \cdot \alpha(T, RH)}{a - \alpha(T, RH)}$$

Where the empirical constants are set to:
- $a = 17.27$
- $b = 237.3\,^\circ\text{C}$

To construct the reference isotherms on the chart matrix, the equation is inverted to solve for relative humidity given a target dew point:

$$RH = 100 \cdot \exp\left(\frac{a \cdot T_d}{b + T_d} - \frac{a \cdot T}{b + T}\right)$$

## Getting Started

Since the application is compiled as a portable, self-contained single-file document, no local web server, Node.js environment, or installation pipelines are required.

1. Clone or copy the `index.html` source code.
2. Save it to your local file system.
3. Double-click the file to execute it natively in any modern compliant web browser (Chrome, Firefox, Edge, Safari).

*Note: An active internet connection is required on initial load to fetch the `Chart.js` library via public CDN.*
