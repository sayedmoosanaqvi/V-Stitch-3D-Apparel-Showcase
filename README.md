V-Stitch is a high-fidelity 3D interactive apparel framework built to solve the "static image" limitation of modern e-commerce. By integrating a cloud-native asset pipeline, the application allows users to interact with detailed 3D models (designed in Blender) with 60FPS performance directly in the web browser.

Technical Challenges & Solutions
This project represents a journey through complex full-stack problem-solving. Below are the key engineering hurdles I overcame:

1. Cloud-Native Asset Pipeline
Problem: 3D models are heavy (~10MB each). Bundling them locally bloated the initial app size and slowed down the web experience.
Solution: Migrated the entire asset library to Firebase Storage.
Result: The application now fetches models dynamically via tokenized HTTPS URLs stored in Firestore, significantly reducing the initial page load time.

2. Resolving the "CORS" Security Block
Problem: Browsers blocked the app from loading 3D data from Firebase because of Cross-Origin Resource Sharing (CORS) restrictions.
Solution: Utilized the Google Cloud Shell to manually configure a custom cors.json policy via the gsutil CLI.
Engineering Feat: This proves my ability to manage low-level cloud security configurations and bridge the gap between frontend and backend infrastructure.

3. Optimizing High-Fidelity Rendering
Problem: Standard web rendering engines struggled with the complex textures and shadows of the Blender models.
Solution: Implemented the CanvasKit renderer and integrated a native model-viewer bridge via web/index.html.
Result: Achieved hardware-accelerated rendering that maintains visual integrity across all desktop and mobile browsers.

Architecture Breakdown
Modeling: High-poly clothing models crafted and optimized in Blender (.glb format).
Frontend: Built with Flutter (Dart) for cross-platform consistency.
Backend: Firebase Authentication for user security and Firestore for real-time product data.
Hosting: Globally distributed via Firebase Hosting with built-in SSL.
