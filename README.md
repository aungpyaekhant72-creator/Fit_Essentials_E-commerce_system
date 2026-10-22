# fit_essentials
# Fit Essentials — Flutter E-commerce (Web + Mobile)
 
A new Flutter project.
Responsive dark-theme supplement store built from the provided UI spec.
Runs on Flutter Web (desktop + mobile web) and compiles for all devices.
 
## Getting Started
## Screens
 
This project is a starting point for a Flutter application.
**Customer side** — Home (hero + featured products), Shop (search, sort,
category/brand/price filters, grid), Product detail (gallery, size, qty,
tabs, Add to Cart / Buy Now), Cart (qty, remove, promo codes, order summary,
free-shipping threshold $100), Checkout (shipping + payment + order create),
Profile (account + order history).
 
A few resources to get you started if this is your first Flutter project:
**Admin side** — Dashboard (KPI cards, 7-day sales chart, recent orders),
Products (table + add/edit/delete + featured + low-stock flags), Orders
(status filter chips + inline status moves), Customers (list + order stats).
 
- [Learn Flutter](https://docs.flutter.dev/get-started/learn-flutter)
- [Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Flutter learning resources](https://docs.flutter.dev/reference/learning-resources)
## Run
 
For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
```bash
flutter pub get
flutter run -d chrome   # or: flutter build web && serve build/web
```
 
## Firebase setup (optional — demo mode without it)
 
Without config the app runs in **demo mode**: any email signs in,
`admin@fitessentials.com` signs in as admin, catalog/orders are in-memory.
 
To connect a real Firebase project:
 
```bash
dart pub global activate flutterfire_cli
flutterfire configure        # regenerates lib/firebase_options.dart
```
 
Then enable in Firebase Console:
 
1. **Authentication → Sign-in method**: Email/Password + Google.
2. **Firestore Database**: create in production mode.
3. Deploy rules: `firebase deploy --only firestore:rules` (see `firestore.rules`).
4. First sign-in with `admin@fitessentials.com` provisions `role: 'admin'`
   on its `users` doc — change `kDemoAdminEmail` in
   `lib/services/auth_service.dart` to use your own admin email.
   For other accounts, set `role: 'admin'` on their `users/{uid}` doc.
5. The catalog auto-seeds on first run when `products` is empty.
 
Schema: `docs/firestore_schema.md`.
 
## Stack
 
Flutter 3.47 / Dart 3.13 · firebase_core 5 · firebase_auth 7 ·
cloud_firestore 7 · google_sign_in 7 · go_router 18 · provider 6 ·
fl_chart 1 · google_fonts 6 · intl.
