<h1 align='center'>Frontend Documentation</h1>
<br>

<h2>Technologies</h2>
<ul>
  <li>React</li>
  <li>TypeScript</li>
  <li>Redux Toolkit</li>
  <li>Styled Components</li>
</ul>

<h2>Deploy</h2>
<ul>
  <li>
    Render — hosting for the frontend as a static site.
  </li>
  <li>
    All <code>/api/*</code> requests are forwarded to the backend via reverse proxy to ensure same‑origin communication.
  </li>
  <li>
    All non-API routes are rewritten to <code>/index.html</code>, enabling the SPA to handle client-side routing.
  </li>
</ul>

<h2>Setup</h2>
<ul>
  <li>
    Vite — provides fast project setup and optimized production builds.  
  </li>
  <li>
    TypeScript config — enforces strict type‑checking and improves project stability.
  </li>
  <li>
    ESLint config — maintains reliable linting rules and consistent code quality.
  </li>
  <li>
    Prettier — ensures uniform formatting across the entire codebase.
  </li>
</ul>

<h2>Architecture</h2>
<ul>
  <li>
    The architecture follows a clean, modular structure with a clear separation of concerns across the application.
  </li>
  <li>
    Core layers are organized in responsibility‑based folders, keeping related functionality logically separated.
  </li>
  <li>
    Barrel files centralize exports, providing consistent and straightforward access to modules within each layer.
  </li>
  <li>
    Global UI elements — modals, loaders, notifications — operate independently from the route‑level rendering tree and are mounted through dedicated portal roots to prevent interference with the main layout.
  </li>
  <li>
    Responsive context — a global context exposes device type and pixel density, allowing components to adapt layout, assets, and behavior dynamically.
  </li>
</ul>

<h2>UX & Accessibility</h2>
<ul>
  <li>
    Loaders — loading indicators maintain an intuitive experience and minimize confusion during ongoing processes.
  </li>
  <li>
    Notifications — instant feedback for key user actions increases reliability and reduces uncertainty.
  </li>
  <li>
    Animations — motion patterns enhance visual perception and create more dynamic, engaging interactions.
  </li>
  <li>
    Transitions — smooth state changes preserve a fluid, natural interface flow.
  </li>
  <li>
    LQIP — blurred low‑quality previews improve perceived loading speed and provide a smoother visual transition.
  </li>
  <li>
    Infinite scroll — additional records are progressively loaded as the user reaches the end of the list.
  </li>
  <li>
    Semantic roles and live regions are applied across the interface to ensure proper announcements for assistive technologies.
  </li>
  <li>
    Keyboard navigation is fully supported, with clear focus-visible states that keep interactions predictable and accessible.
  </li>
  <li>
    Modal interactions follow accessible patterns, including controlled focus handling, consistent dismissal logic, and complete isolation from the underlying layout.
  </li>
  <li>
    Form behavior enables a guided submission flow, helping users enter information confidently while the interface manages validation, limits, and action availability.
  </li>
</ul>

<h2>UI & Styling</h2>
<ul>
  <li>
    Styling is managed with styled‑components, providing predictable behavior, clean component structure, and fully scoped styles.
  </li>
  <li>
    Cross‑browser compatibility — a unified styling baseline is achieved through modern‑normalize, refined global reset rules, and targeted vendor prefixes to ensure uniform rendering across browsers.
  </li>
  <li>
    Responsive design — built on a mobile‑first foundation, the interface adapts seamlessly across devices and screen sizes.
  </li>
  <li>
    Responsive imagery — images are served in 1x/2x resolutions and breakpoint‑specific variants for optimal visual quality on all displays.
  </li>
  <li>
    Cloud‑hosted media — images and videos are delivered through Cloudinary, benefiting from automatic format optimization, smart compression, CDN‑level performance, and zero local storage overhead.
  </li>
  <li>
    Images are manually optimized with Squoosh, converted to modern WebP formats, and compressed to achieve a balanced quality–size ratio.
  </li>
  <li>
    Videos are processed with HandBrake and re‑encoded using H.264 to ensure reduced file size and reliable cross‑browser playback.
  </li>
  <li>
    Sprite technique — all vector icons are consolidated into a single SVG sprite to reduce network requests and keep icon management consistent and efficient.
  </li>
</ul>

<h2>Routing</h2>
<ul>
  <li>
    The project runs as a Single Page Application, with React Router managing all client‑side navigation.
  </li>
  <li>
    Restricted routes — pages accessible only when the user is not authenticated, with a redirect guard preventing access once a session is active.
  </li>
  <li>
    Protected routes — core application pages become available only after authentication, and unauthorized access is automatically redirected to the login flow.
  </li>
  <li>
    Fallback route — any unmatched path is routed to a dedicated Not Found page, ensuring consistent handling of invalid URLs.
  </li>
</ul>

<h2>State Management</h2>
<ul>
  <li>
    Redux — manages the application’s global state in a predictable and centralized way.
  </li>
  <li>
    Redux Toolkit — simplifies the Redux setup with slice‑based logic and reduced boilerplate.
  </li>
  <li>
    Redux Persist — preserves the application state across page reloads.
  </li>
</ul>

<h2>API Layer</h2>
<ul>   
  <li>
    The API Layer is built on a dedicated Axios client instance that centralizes all communication with the backend.
  </li>
  <li>
    Request interceptor — looks for the session token in session storage and attaches it to the Authorization header as a Bearer token.
  </li>
  <li>
    Response interceptor — stores the session token when the server returns one and triggers an automatic logout when a 401 error occurs.
  </li>
  <li>
    Session logic — the server issues secure HTTP‑Only cookies to handle authentication and assigns each browser tab a unique session identifier, ensuring a single active session per user and proper isolation across tabs.
  </li>
</ul>

<h2>Other Details</h2>
<ul>
  <li>
    Request orchestration — asynchronous operations are processed within a unified flow that centralizes response handling, synchronizes global loading, and applies artificial delays to avoid flickering.
  </li>
  <li>
    Input debouncing — input changes are debounced to limit update frequency, reduce unnecessary re-renders, and maintain interface responsiveness.
  </li>
  <li>
    Validation system — all form validation rules are defined in a declarative map, which is used to dynamically generate Yup schemas that enforce input correctness and prevent invalid payloads from reaching the server.
  </li>
  <li>
    Browser storage — data can be persisted in local or session storage through a custom hook that applies user ownership and TTL‑based invalidation.
  </li>
  <li>
    Preconnect and DNS-prefetch directives optimize connection setup for Google Fonts and Cloudinary assets.
  </li>
</ul>
