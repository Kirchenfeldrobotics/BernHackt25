# Meal-Cam

Projekt vom BärnHäckt 2025 (22.–24. August 2025), Team Kirchenfeldrobotics: Jakob, Phileas, Nick, Nils und Valery.

Man fotografiert ein Lebensmittel, die Google Cloud Vision API erkennt es, und die App schlägt
dazu passende Rezepte von TheMealDB vor. Erkannte Produkte und gespeicherte Menüs liegen in
Firestore, dazu gibt es einen Wochenplan (noch mit Beispieldaten).

Das Projekt besteht aus zwei Teilen:

- `mobile_application/` – Flutter-App mit Riverpod und Firebase
- `server/` – Flask-API, lief am Hackathon auf einem Raspberry Pi 5

## Server starten

```sh
cd server
pip install -r requirements.txt
export GOOGLE_VISION_KEY_PATH=/pfad/zu/service-account.json
python api.py
```

Der Service-Account-Key für Google Cloud Vision liegt nicht im Repository und muss selbst
hinterlegt werden. Die API läuft auf Port 5000:

| Endpunkt | Zweck |
| --- | --- |
| `POST /analyze` | Bild hochladen, erkanntes Label zurückgeben |
| `GET /meals/category/<kategorie>` | Menüs einer Kategorie |
| `GET /meals/search/<name>` | Menüs nach Namen suchen |
| `GET /meals/details/<id>` | Details zu einem Menü |
| `GET /meals/image/<id>` | Bild-URL zu einem Menü |

## App starten

```sh
cd mobile_application
flutter pub get
flutter run
```

Die Server-Adresse steht in `mobile_application/lib/services/api.dart` (`apiUrl`) und muss auf
die eigene Server-IP angepasst werden.

## Dokumentation

In `documents/` liegen der Pitch, die technische Dokumentation und der Screencast.

## Lizenz

PolyForm Noncommercial License 1.0.0: Nutzung, Änderung und Weitergabe sind für
nicht-kommerzielle Zwecke erlaubt, Details in [LICENSE](LICENSE).

## Organisation

Danke an das Team von BärnHäckt für den Hackathon.
