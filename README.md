# s6-frontend

Dit is de frontend voor het microservicesproject. De applicatie is gebouwd in **Vue 3** (Vite) en communiceert met de backend via de API Gateway.

---

## 📦 Installatie

Eerst de dependencies installeren:

```bash
npm install
```

---

## 🚀 Development Server

Start de Vite-devserver:

```bash
npm run dev
```

De frontend draait standaard op:

```
http://localhost:5173
```

---

## 🔗 Backend-verbinding

Alle API-calls worden gedaan naar:

```
http://localhost:8080/api/...
```

Voorbeeld met axios:

```javascript
axios.get("http://localhost:8080/api/music")
```

De gateway handelt routing én CORS af.
