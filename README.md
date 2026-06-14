# 🏆 Polla Mundialista 2026

Aplicación web de **quiniela (polla) para el Mundial FIFA 2026**. Familia, amigos o compañeros
de trabajo crean su grupo, hacen sus predicciones y compiten por el primer lugar — con
**resultados que se sincronizan en tiempo real** entre todos los dispositivos.

🔗 **App en vivo:** desplegada en Netlify · 📱 funciona en celular y computadora

---

## ✨ Qué hace

- **Crear un grupo** e invitar a la familia/amigos a la misma polla.
- **Predicciones completas** de los 48 equipos del Mundial 2026:
  - Clasificados de cada grupo
  - Avance por rondas (16avos → octavos → cuartos → semis)
  - **Campeón, subcampeón, 3º, 4º puesto y goleador**
- **Ranking automático** que recalcula los puntos de cada participante en vivo.
- **Resultados en tiempo real** sincronizados automáticamente desde **API-Football**
  (posiciones, partidos finalizados y tabla de goleadores).
- **Panel de administración** protegido con contraseña para cargar/ajustar resultados manualmente.

## 🧮 Sistema de puntos

| Logro | Puntos |
|---|---|
| Equipo pasa a 16avos | +1 |
| Equipo pasa a octavos | +1 |
| Equipo pasa a cuartos | +1 |
| Equipo llega a semifinales | +1 |
| Acertar 4º puesto | +2 extra |
| Acertar 3er puesto | +4 extra |
| Acertar subcampeón | +6 extra |
| Acertar campeón 🏆 | +10 extra |
| Acertar goleador ⚽ | +5 bonus |

## 🗄️ Almacenamiento de datos (arquitectura)

La app guarda la información con un esquema de **doble respaldo**:

1. **Firebase Realtime Database** — base de datos en la **nube en tiempo real**. Cuando alguien
   guarda su polla o se actualiza un resultado, **todos los participantes lo ven al instante**
   en sus propios dispositivos. Es lo que permite jugar en familia sin estar en la misma máquina.
2. **localStorage (respaldo offline)** — si no hay conexión con Firebase, la app sigue funcionando
   y guarda los datos localmente en el navegador, para no perder nada.

```
Guardar polla / resultado
        │
        ├─►  Firebase Realtime Database   (nube · sincroniza a todos en tiempo real)
        └─►  localStorage                 (respaldo local · modo offline)
```

## 🛠️ Tecnologías

- **Frontend:** HTML + CSS + JavaScript (vanilla, single-page app, sin frameworks)
- **Base de datos:** Firebase Realtime Database (SDK 8.10.1)
- **Resultados deportivos:** API-Football (REST)
- **Despliegue:** Netlify
- **SEO:** metadatos Open Graph / Twitter, `schema.org`, `robots.txt` y `sitemap.xml`

## 📂 Archivos

| Archivo | Descripción |
|---|---|
| `index.html` | Aplicación completa (UI + lógica + Firebase + scoring) |
| `fifa2026.png` | Logo del Mundial |
| `logo.jpg` | Logo de la polla |
| `robots.txt` · `sitemap.xml` | SEO |

## 🚀 Cómo usarla

1. Abre `index.html` en cualquier navegador (o entra a la URL de Netlify).
2. Escribe tu nombre y crea/únete a tu grupo.
3. Haz tus predicciones y guarda.
4. A medida que avanza el Mundial, el ranking se actualiza solo.

> **Configuración (para reutilizar el proyecto):** la app necesita tus propias credenciales de
> **Firebase** (objeto `FIREBASE_CONFIG`) y tu **API key de API-Football**. Por seguridad, usa tus
> propias claves y restringe el acceso a tu base de datos desde la consola de Firebase.

---

Hecho con ❤️ por **Daniela Chávez** para la familia.
