# 🤝 Guida per Contribuire a White Hacker Simulator

Prima di tutto, **grazie** per voler contribuire! ❤️

Questo progetto esiste grazie a persone come te. Ogni contributo, grande o piccolo, è prezioso.

---

## 📋 Indice

- [Codice di Condotta](#-codice-di-condotta)
- [Come Posso Contribuire?](#-come-posso-contribuire)
- [Setup Ambiente](#-setup-ambiente)
- [Workflow di Sviluppo](#-workflow-di-sviluppo)
- [Linee Guida Codice](#-linee-guida-codice)
- [Creare Missioni](#-creare-missioni)
- [Traduzioni](#-traduzioni)
- [Riconoscimenti](#-riconoscimenti)

---

## 📜 Codice di Condotta

Partecipando a questo progetto, accetti di mantenere un ambiente rispettoso e inclusivo. 

Leggi il nostro [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) completo.

**In breve:**
- ✅ Sii rispettoso e inclusivo
- ✅ Accetta feedback costruttivo
- ✅ Concentrati su ciò che è meglio per la community
- ❌ Nessuna molestia, discriminazione o comportamento tossico

---

## 🎯 Come Posso Contribuire?

### 🐛 Segnalare Bug

Hai trovato un bug? Apri una [issue](../../issues/new?template=bug_report.md)!

**Prima di segnalare:**
1. Controlla che non sia già stato segnalato
2. Usa l'ultima versione del gioco
3. Includi passi per riprodurre il bug

### 💡 Proporre Feature

Hai un'idea? Fantastico! Apri una [issue](../../issues/new?template=feature_request.md)!

**Includi:**
- Descrizione chiara della feature
- Perché sarebbe utile
- Possibili implementazioni

### 🎮 Creare Missioni/Sfide

Vuoi creare contenuti per il gioco? Vedi la sezione [Creare Missioni](#-creare-missioni).

### 🌍 Tradurre

Parli altre lingue? Aiutaci a tradurre! Vedi sezione [Traduzioni](#-traduzioni).

### 💻 Scrivere Codice

Pronto a programmare? Continua a leggere!

---

## 🔧 Setup Ambiente

### Prerequisiti

- **Node.js** 18+ ([download](https://nodejs.org/))
- **Git** ([download](https://git-scm.com/))
- **Editor**: VS Code consigliato ([download](https://code.visualstudio.com/))

### Installazione

```bash
# 1. Forka il repository su GitHub (bottone "Fork" in alto a destra)

# 2. Clona il tuo fork
git clone https://github.com/[TUO-USERNAME]/white-hacker-simulator.git
cd white-hacker-simulator

# 3. Aggiungi l'upstream (repository originale)
git remote add upstream https://github.com/[OWNER]/white-hacker-simulator.git

# 4. Installa le dipendenze
npm install

# 5. Crea file configurazione locale
cp .env.example .env.local

# 6. Avvia in modalità sviluppo
npm run dev
```

### Struttura Progetto

```
white-hacker-simulator/
├── 📁 src/
│   ├── 📁 main/           # Processo principale Electron
│   ├── 📁 renderer/       # UI React
│   │   ├── 📁 components/ # Componenti riutilizzabili
│   │   ├── 📁 pages/      # Pagine/schermate
│   │   ├── 📁 hooks/      # React hooks custom
│   │   ├── 📁 stores/     # State management
│   │   └── 📁 utils/      # Utility functions
│   ├── 📁 game/           # Logica di gioco
│   │   ├── 📁 missions/   # Sistema missioni
│   │   ├── 📁 ai/         # Integrazione IA
│   │   ├── 📁 economy/    # Sistema economico
│   │   └── 📁 story/      # Sistema narrativo
│   └── 📁 shared/         # Codice condiviso
├── 📁 assets/             # Immagini, suoni, font
├── 📁 content/            # Missioni, dialoghi, dati
├── 📁 locales/            # File traduzioni
├── 📁 docs/               # Documentazione
└── 📁 tests/              # Test automatici
```

---

## 🔄 Workflow di Sviluppo

### 1. Sincronizza con Upstream

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

### 2. Crea un Branch

```bash
# Per feature
git checkout -b feature/nome-feature

# Per bugfix
git checkout -b fix/descrizione-bug

# Per documentazione
git checkout -b docs/cosa-documenti
```

### 3. Sviluppa

- Scrivi codice seguendo le [linee guida](#-linee-guida-codice)
- Testa le modifiche: `npm run test`
- Committa spesso con messaggi chiari

### 4. Commit Messages

Usa il formato **Conventional Commits**:

```
tipo(scope): descrizione breve

[corpo opzionale]

[footer opzionale]
```

**Tipi:**
- `feat`: Nuova feature
- `fix`: Bug fix
- `docs`: Documentazione
- `style`: Formattazione (no cambio logica)
- `refactor`: Refactoring codice
- `test`: Aggiunta/modifica test
- `chore`: Manutenzione, dipendenze

**Esempi:**
```
feat(missions): aggiunta missione phishing base
fix(terminal): corretto bug copia-incolla su Linux
docs(readme): aggiornata sezione installazione
```

### 5. Apri Pull Request

1. Pusha il branch: `git push origin feature/nome-feature`
2. Vai su GitHub e clicca "Compare & Pull Request"
3. Compila il template PR
4. Attendi review

### 6. Code Review

- Rispondi ai commenti
- Fai modifiche se richieste
- Una volta approvata, verrà mergiata!

---

## 📝 Linee Guida Codice

### TypeScript

```typescript
// ✅ Buono: tipi espliciti per funzioni pubbliche
function calculateDamage(attack: number, defense: number): number {
  return Math.max(0, attack - defense);
}

// ❌ Evita: any
function doSomething(data: any) { ... }

// ✅ Meglio: tipo specifico o generic
function doSomething(data: T): T { ... }
```

### React Components

```tsx
// ✅ Buono: componente funzionale con tipi
interface ButtonProps {
  label: string;
  onClick: () => void;
  variant?: 'primary' | 'secondary';
}

export function Button({ label, onClick, variant = 'primary' }: ButtonProps) {
  return (
    
      {label}
    
  );
}
```

### Stile Codice

- **Indentazione**: 2 spazi
- **Punto e virgola**: Sì
- **Quote**: Singole per JS/TS, doppie per JSX
- **Max lunghezza riga**: 100 caratteri

ESLint e Prettier sono configurati. Esegui prima di committare:

```bash
npm run lint      # Controlla errori
npm run format    # Formatta automaticamente
```

### Naming Conventions

| Tipo | Convenzione | Esempio |
|------|-------------|---------|
| Variabili/funzioni | camelCase | `playerScore`, `calculateDamage()` |
| Componenti React | PascalCase | `PlayerProfile`, `MissionCard` |
| Costanti | UPPER_SNAKE | `MAX_LEVEL`, `API_ENDPOINT` |
| File componenti | PascalCase.tsx | `PlayerProfile.tsx` |
| File utility | camelCase.ts | `formatDate.ts` |
| CSS classes | kebab-case | `player-profile`, `mission-card` |

---

## 🎮 Creare Missioni

Vuoi creare nuove missioni? Fantastico!

### Struttura Missione

Le missioni sono definite in file YAML in `content/missions/`:

```yaml
# content/missions/tutorial/phishing-101.yaml

id: "phishing-101"
title: "Riconosci il Phishing"
description: "Impara a identificare email fraudolente"
difficulty: 1
category: "social-engineering"
xp_reward: 100
credits_reward: 50

# Requisiti per sbloccare
requirements:
  min_level: 1
  completed_missions: []

# Obiettivi della missione
objectives:
  - id: "analyze_email"
    description: "Analizza l'email sospetta"
    type: "interact"
    target: "email_suspicious_1"
    
  - id: "identify_red_flags"
    description: "Identifica 3 segnali di phishing"
    type: "find"
    count: 3
    
  - id: "report_phishing"
    description: "Segnala l'email come phishing"
    type: "action"
    action: "report_phishing"

# Contenuto della missione
content:
  emails:
    - id: "email_suspicious_1"
      from: "security@g00gle.com"  # Nota: 00 invece di oo
      subject: "URGENTE: Il tuo account è stato compromesso"
      body: |
        Gentile utente,
        
        Abbiamo rilevato attività sospetta sul tuo account.
        Clicca qui IMMEDIATAMENTE per verificare la tua identità:
        
        http://google-security-check.totallylegit.com/verify
        
        Se non agisci entro 24 ore, il tuo account verrà sospeso.
        
        Google Security Team
      
      red_flags:
        - "mittente: g00gle.com invece di google.com"
        - "url: dominio sospetto non ufficiale"
        - "urgenza: pressione psicologica"
        - "minaccia: conseguenze esagerate"
        - "grammatica: errori sottili"

# Dialoghi ARIA
aria_dialogues:
  start: "Hai ricevuto un'email strana. Analizziamola insieme!"
  hint_1: "Guarda attentamente l'indirizzo del mittente..."
  hint_2: "Quel link ti sembra legittimo?"
  success: "Ottimo lavoro! Hai identificato tutti i segnali di phishing."
  
# Spiegazione post-missione
debrief:
  title: "Cosa hai imparato"
  content: |
    Il phishing è una delle tecniche più comuni usate dai criminali.
    
    **Segnali da cercare:**
    - Mittenti sospetti (controlla sempre il dominio!)
    - URL che non corrispondono al sito ufficiale
    - Senso di urgenza e minacce
    - Richieste di dati personali
    
    **Come proteggersi:**
    - Non cliccare link in email sospette
    - Vai direttamente sul sito ufficiale
    - Verifica con l'azienda se hai dubbi
```

### Guida Completa

Leggi [docs/MISSION_CREATION.md](docs/MISSION_CREATION.md) per la guida completa.

---

## 🌍 Traduzioni

### File di Traduzione

Le traduzioni sono in `locales/[lingua]/`:

```
locales/
├── it/           # Italiano (principale)
│   ├── common.json
│   ├── missions.json
│   ├── ui.json
│   └── story.json
├── en/           # Inglese
│   └── ...
└── es/           # Spagnolo (esempio)
    └── ...
```

### Formato

```json
// locales/it/ui.json
{
  "menu": {
    "play": "Gioca",
    "settings": "Impostazioni",
    "quit": "Esci"
  },
  "game": {
    "level": "Livello",
    "xp": "Esperienza",
    "mission_complete": "Missione completata!"
  }
}
```

### Come Tradurre

1. Copia la cartella `locales/en/` in `locales/[tua-lingua]/`
2. Traduci i file JSON
3. Apri una PR con titolo: `feat(i18n): add [lingua] translation`

---

## 🏆 Riconoscimenti

Ogni contributore viene riconosciuto:

### Nel Gioco
- Nome nei **Credits**
- Badge speciale **"Contributor"** se giochi
- Accesso anticipato a nuove feature

### Su GitHub
- Aggiunto a **CONTRIBUTORS.md**
- Menzione nelle **Release Notes**
- Badge sul profilo (GitHub contributor)

### Contributori Speciali
- **Top Contributors**: Menzione speciale e ruolo Discord
- **Core Team**: Per chi contribuisce regolarmente

---

## ❓ Domande?

- 💬 **Discord**: [Link al server](#)
- 📧 **Email**: whitehackersim@email.com
- 🗨️ **Discussions**: [GitHub Discussions](../../discussions)

Non esitare a chiedere! Siamo qui per aiutarti.

---

## 🙏 Grazie!

Ogni riga di codice, ogni traduzione, ogni bug report ci avvicina all'obiettivo: **insegnare la cybersecurity a tutti**.

Grazie per far parte di questa missione! 🚀

---

<p align="center">
  <strong>Happy Hacking! 🎮🔐</strong>
</p>