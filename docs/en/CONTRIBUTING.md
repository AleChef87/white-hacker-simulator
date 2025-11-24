# 🤝 Contributing to White Hacker Simulator

First of all, **thank you** for wanting to contribute! ❤️

This project exists thanks to people like you. Every contribution, big or small, is valuable.

---

## 📋 Table of Contents

- [Code of Conduct](#-code-of-conduct)
- [How Can I Contribute?](#-how-can-i-contribute)
- [Environment Setup](#-environment-setup)
- [Development Workflow](#-development-workflow)
- [Code Guidelines](#-code-guidelines)
- [Creating Missions](#-creating-missions)
- [Translations](#-translations)
- [Recognition](#-recognition)

---

## 📜 Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment.

Read our full [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

**In short:**
- ✅ Be respectful and inclusive
- ✅ Accept constructive feedback gracefully
- ✅ Focus on what's best for the community
- ❌ No harassment, discrimination, or toxic behavior

---

## 🎯 How Can I Contribute?

### 🐛 Report Bugs

Found a bug? Open an [issue](../../issues/new?template=bug_report.md)!

**Before reporting:**
1. Check it hasn't already been reported
2. Use the latest version of the game
3. Include steps to reproduce the bug

### 💡 Propose Features

Have an idea? Great! Open an [issue](../../issues/new?template=feature_request.md)!

**Include:**
- Clear description of the feature
- Why it would be useful
- Possible implementations

### 🎮 Create Missions/Challenges

Want to create game content? See the [Creating Missions](#-creating-missions) section.

### 🌍 Translate

Speak other languages? Help us translate! See [Translations](#-translations) section.

### 💻 Write Code

Ready to code? Keep reading!

---

## 🔧 Environment Setup

### Prerequisites

- **Node.js** 18+ ([download](https://nodejs.org/))
- **Git** ([download](https://git-scm.com/))
- **Editor**: VS Code recommended ([download](https://code.visualstudio.com/))

### Installation

```bash
# 1. Fork the repository on GitHub (click "Fork" button top right)

# 2. Clone your fork
git clone https://github.com/[YOUR-USERNAME]/white-hacker-simulator.git
cd white-hacker-simulator

# 3. Add upstream (original repository)
git remote add upstream https://github.com/[OWNER]/white-hacker-simulator.git

# 4. Install dependencies
npm install

# 5. Create local configuration file
cp .env.example .env.local

# 6. Start in development mode
npm run dev
```

### Project Structure

```
white-hacker-simulator/
├── 📁 src/
│   ├── 📁 main/           # Electron main process
│   ├── 📁 renderer/       # React UI
│   │   ├── 📁 components/ # Reusable components
│   │   ├── 📁 pages/      # Pages/screens
│   │   ├── 📁 hooks/      # Custom React hooks
│   │   ├── 📁 stores/     # State management
│   │   └── 📁 utils/      # Utility functions
│   ├── 📁 game/           # Game logic
│   │   ├── 📁 missions/   # Mission system
│   │   ├── 📁 ai/         # AI integration
│   │   ├── 📁 economy/    # Economic system
│   │   └── 📁 story/      # Narrative system
│   └── 📁 shared/         # Shared code
├── 📁 assets/             # Images, sounds, fonts
├── 📁 content/            # Missions, dialogues, data
├── 📁 locales/            # Translation files
├── 📁 docs/               # Documentation
└── 📁 tests/              # Automated tests
```

---

## 🔄 Development Workflow

### 1. Sync with Upstream

```bash
git fetch upstream
git checkout main
git merge upstream/main
```

### 2. Create a Branch

```bash
# For features
git checkout -b feature/feature-name

# For bugfixes
git checkout -b fix/bug-description

# For documentation
git checkout -b docs/what-you-document
```

### 3. Develop

- Write code following the [guidelines](#-code-guidelines)
- Test your changes: `npm run test`
- Commit often with clear messages

### 4. Commit Messages

Use **Conventional Commits** format:

```
type(scope): short description

[optional body]

[optional footer]
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation
- `style`: Formatting (no logic change)
- `refactor`: Code refactoring
- `test`: Adding/modifying tests
- `chore`: Maintenance, dependencies

**Examples:**
```
feat(missions): add basic phishing mission
fix(terminal): fixed copy-paste bug on Linux
docs(readme): updated installation section
```

### 5. Open Pull Request

1. Push your branch: `git push origin feature/feature-name`
2. Go to GitHub and click "Compare & Pull Request"
3. Fill in the PR template
4. Wait for review

### 6. Code Review

- Respond to comments
- Make changes if requested
- Once approved, it will be merged!

---

## 📝 Code Guidelines

### TypeScript

```typescript
// ✅ Good: explicit types for public functions
function calculateDamage(attack: number, defense: number): number {
  return Math.max(0, attack - defense);
}

// ❌ Avoid: any
function doSomething(data: any) { ... }

// ✅ Better: specific type or generic
function doSomething<T>(data: T): T { ... }
```

### React Components

```tsx
// ✅ Good: functional component with types
interface ButtonProps {
  label: string;
  onClick: () => void;
  variant?: 'primary' | 'secondary';
}

export function Button({ label, onClick, variant = 'primary' }: ButtonProps) {
  return (
    <button 
      className={`btn btn-${variant}`}
      onClick={onClick}
    >
      {label}
    </button>
  );
}
```

### Code Style

- **Indentation**: 2 spaces
- **Semicolons**: Yes
- **Quotes**: Single for JS/TS, double for JSX
- **Max line length**: 100 characters

ESLint and Prettier are configured. Run before committing:

```bash
npm run lint      # Check errors
npm run format    # Auto-format
```

### Naming Conventions

| Type | Convention | Example |
|------|------------|---------|
| Variables/functions | camelCase | `playerScore`, `calculateDamage()` |
| React components | PascalCase | `PlayerProfile`, `MissionCard` |
| Constants | UPPER_SNAKE | `MAX_LEVEL`, `API_ENDPOINT` |
| Component files | PascalCase.tsx | `PlayerProfile.tsx` |
| Utility files | camelCase.ts | `formatDate.ts` |
| CSS classes | kebab-case | `player-profile`, `mission-card` |

---

## 🎮 Creating Missions

Want to create new missions? Awesome!

### Mission Structure

Missions are defined in YAML files in `content/missions/`:

```yaml
# content/missions/tutorial/phishing-101.yaml

id: "phishing-101"
title: "Recognize Phishing"
description: "Learn to identify fraudulent emails"
difficulty: 1
category: "social-engineering"
xp_reward: 100
credits_reward: 50

objectives:
  - id: "analyze_email"
    description: "Analyze the suspicious email"
    type: "interact"
    target: "email_suspicious_1"

# ... see full guide in docs/MISSION_CREATION.md
```

### Full Guide

Read [docs/MISSION_CREATION.md](MISSION_CREATION.md) for the complete guide.

---

## 🌍 Translations

### Translation Files

Translations are in `locales/[language]/`:

```
locales/
├── en/           # English
│   ├── common.json
│   ├── missions.json
│   └── ui.json
├── it/           # Italian
│   └── ...
└── es/           # Spanish (example)
    └── ...
```

### How to Translate

1. Copy the `locales/en/` folder to `locales/[your-language]/`
2. Translate the JSON files
3. Open a PR with title: `feat(i18n): add [language] translation`

---

## 🏆 Recognition

Every contributor is recognized:

### In the Game
- Name in **Credits**
- Special **"Contributor"** badge if you play
- Early access to new features

### On GitHub
- Added to **CONTRIBUTORS.md**
- Mentioned in **Release Notes**
- Profile badge (GitHub contributor)

### Special Contributors
- **Top Contributors**: Special mention and Discord role
- **Core Team**: For those who contribute regularly

---

## ❓ Questions?

- 💬 **Discord**: [Server link](#)
- 📧 **Email**: whitehackersim@email.com
- 🗨️ **Discussions**: [GitHub Discussions](../../discussions)

Don't hesitate to ask! We're here to help.

---

## 🙏 Thank You!

Every line of code, every translation, every bug report brings us closer to the goal: **teaching cybersecurity to everyone**.

Thank you for being part of this mission! 🚀

---

<p align="center">
  <strong>Happy Hacking! 🎮🔐</strong>
</p>
