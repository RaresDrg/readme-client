Frontend Documentation

Technologies
React
TypeScript
Redux Toolkit
Styled Components
Deploy
Render — hosting for the frontend as a static site.
All /api/* requests are forwarded to the backend via reverse proxy to ensure same‑origin communication.
All non-API routes are rewritten to /index.html, enabling the SPA to handle client-side routing.
Setup
Vite — provides fast project setup and optimized production builds.
TypeScript config — enforces strict type‑checking and improves project stability.
ESLint config — maintains reliable linting rules and consistent code quality.
Prettier — ensures uniform formatting across the entire codebase.
Architecture
The architecture follows a clean, modular structure with a clear separation of concerns across the application.
Core layers are organized in responsibility‑based folders, keeping related functionality logically separated.
Barrel files centralize exports, providing consistent and straightforward access to modules within each layer.
Global UI elements — modals, loaders, notifications — operate independently from the route‑level rendering tree and are mounted through dedicated portal roots to prevent interference with the main layout.
Responsive context — a global context exposes device type and pixel density, allowing components to adapt layout, assets, and behavior dynamically.
UX & Accessibility
Loaders — loading indicators maintain an intuitive experience and minimize confusion during ongoing processes.
Notifications — instant feedback for key user actions increases reliability and reduces uncertainty.
Animations — motion patterns enhance visual perception and create more dynamic, engaging interactions.
Transitions — smooth state changes preserve a fluid, natural interface flow.
LQIP — blurred low‑quality previews improve perceived loading speed and provide a smoother visual transition.
Infinite scroll — additional records are progressively loaded as the user reaches the end of the list.
Semantic roles and live regions are applied across the interface to ensure proper announcements for assistive technologies.
Keyboard navigation is fully supported, with clear focus-visible states that keep interactions predictable and accessible.
Modal interactions follow accessible patterns, including controlled focus handling, consistent dismissal logic, and complete isolation from the underlying layout.
Form behavior enables a guided submission flow, helping users enter information confidently while the interface manages validation, limits, and action availability.
UI & Styling
Styling is managed with styled‑components, providing predictable behavior, clean component structure, and fully scoped styles.
Cross‑browser compatibility — a unified styling baseline is achieved through modern‑normalize, refined global reset rules, and targeted vendor prefixes to ensure uniform rendering across browsers.
Responsive design — built on a mobile‑first foundation, the interface adapts seamlessly across devices and screen sizes.
Responsive imagery — images are served in 1x/2x resolutions and breakpoint‑specific variants for optimal visual quality on all displays.
Cloud‑hosted media — images and videos are delivered through Cloudinary, benefiting from automatic format optimization, smart compression, CDN‑level performance, and zero local storage overhead.
Images are manually optimized with Squoosh, converted to modern WebP formats, and compressed to achieve a balanced quality–size ratio.
Videos are processed with HandBrake and re‑encoded using H.264 to ensure reduced file size and reliable cross‑browser playback.
Sprite technique — all vector icons are consolidated into a single SVG sprite to reduce network requests and keep icon management consistent and efficient.
Routing
The project runs as a Single Page Application, with React Router managing all client‑side navigation.
Restricted routes — pages accessible only when the user is not authenticated, with a redirect guard preventing access once a session is active.
Protected routes — core application pages become available only after authentication, and unauthorized access is automatically redirected to the login flow.
Fallback route — any unmatched path is routed to a dedicated Not Found page, ensuring consistent handling of invalid URLs.
State Management
Redux — manages the application’s global state in a predictable and centralized way.
Redux Toolkit — simplifies the Redux setup with slice‑based logic and reduced boilerplate.
Redux Persist — preserves the application state across page reloads.
API Layer
The API Layer is built on a dedicated Axios client instance that centralizes all communication with the backend.
Request interceptor — looks for the session token in session storage and attaches it to the Authorization header as a Bearer token.
Response interceptor — stores the session token when the server returns one and triggers an automatic logout when a 401 error occurs.
Session logic — the server issues secure HTTP‑Only cookies to handle authentication and assigns each browser tab a unique session identifier, ensuring a single active session per user and proper isolation across tabs.
Other Details
Request orchestration — asynchronous operations are processed within a unified flow that centralizes response handling, synchronizes global loading, and applies artificial delays to avoid flickering.
Input debouncing — input changes are debounced to limit update frequency, reduce unnecessary re-renders, and maintain interface responsiveness.
Validation system — all form validation rules are defined in a declarative map, which is used to dynamically generate Yup schemas that enforce input correctness and prevent invalid payloads from reaching the server.
Browser storage — data can be persisted in local or session storage through a custom hook that applies user ownership and TTL‑based invalidation.
Preconnect and DNS-prefetch directives optimize connection setup for Google Fonts and Cloudinary assets.
