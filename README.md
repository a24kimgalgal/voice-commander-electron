# Activitat 3: Interfície Natural (Control per Veu)

Aquest projecte és una **Prova de Concepte (PoC)** d'una interfície d'usuari natural (VUI) desenvolupada amb **Electron**, **Vue 3** i **Vuetify**. L'aplicació permet controlar l'estat de la interfície i el tema visual mitjançant comandes de veu, utilitzant la **Web Speech API** nativa.

## Característiques

- **Reconeixement de Veu:** Ús de `webkitSpeechRecognition` encapsulat en un Vue Composable.
- **Gestió de Permisos:** Configuració d'Electron per permetre l'accés al micròfon automàticament.
- **Feedback Visual:**
  - Animació de "pols" quan el micròfon està actiu.
  - Transcripció en temps real (Interim Results).
  - **Snackbar d'error** quan no s'entén una comanda.
- **Control de Tema:** Canvi entre *Mode Clar* i *Mode Fosc* per veu.

## Demostració

Aquí es pot veure el funcionament del canvi de tema i la gestió d'errors:

Tema Clar:
<img width="1919" height="949" alt="TemaClar" src="https://github.com/user-attachments/assets/b6d99f60-82cb-46ce-ad24-61e46ff08dbf" />

Gestió d'errors:
<img width="1885" height="938" alt="Error" src="https://github.com/user-attachments/assets/35427bcc-821d-4962-a2f5-7b6508235e25" />


## Guia de Comandes

L'aplicació respon a les següents paraules clau (en català):

| Comanda de Veu | Acció | Resultat Visual |
| :--- | :--- | :--- |
| **"Saluda"** | Saluda l'usuari | Missatge de benvinguda en verd (Success) |
| **"Ajuda"** | Mostra informació | Missatge informatiu en blau (Info) |
| **"Mode Fosc"** | Canvia el tema | Tota l'aplicació passa a colors foscos |
| **"Mode Clar"** | Canvia el tema | L'aplicació torna a colors clars |
| **"Esborra"** | Reinicia l'estat | Torna al missatge inicial "En espera" |
| *Paraula no reconeguda*| Gestió d'errors | Mostra un **Snackbar vermell** amb el text entès |

## Instal·lació i Execució

Requisits previs: Tenir instal·lat **Node.js** i **NPM**.

1. **Clonar el repositori:**
   ```bash
   git clone [https://github.com/a24kimgalgal/voice-commander-electron.git](https://github.com/a24kimgalgal/voice-commander-electron.git)
   cd voice-commander-electron

## Nota sobre l'API de Veu en Electron

L'aplicació funciona perfectament en navegador (Chrome via localhost). 
No obstant això, en l'executable d'Electron pot aparèixer un `NetworkError` al utilitzar el micròfon.

**Motiu tècnic:** L'API `webkitSpeechRecognition` utilitza els servidors de Google per al processament. Google restringeix l'accés a aquesta API des de Chromium/Electron si no es configuren claus d'API de Google Cloud (que requereixen facturació). El codi és funcional, però el servei extern bloqueja la petició des de l'entorn d'escriptori sense credencials.
