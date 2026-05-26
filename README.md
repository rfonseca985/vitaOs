# 🌿 vitaOS - Intelligent Telemedicine Platform

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-14-black?style=flat-square&logo=next.js" />
  <img src="https://img.shields.io/badge/TypeScript-5-blue?style=flat-square&logo=typescript" />
  <img src="https://img.shields.io/badge/Prisma-PostgreSQL-2d2d2d?style=flat-square&logo=prisma" />
  <img src="https://img.shields.io/badge/Tailwind-3.4-38bdf8?style=flat-square&logo=tailwindcss" />
  <img src="https://img.shields.io/badge/OpenAI-GPT--4-412991?style=flat-square&logo=openai" />
</p>

> **Plataforma de telemedicina completa com IA integrada. Conectando pacientes a médicos qualificados com segurança, tecnologia e inteligência artificial.**

---

## 📋 Table of Contents / Índice

- [🇧🇷 Português](#-português)
- [🇺🇸 English](#-english)

---

# 🇧🇷 Português

## 🚀 Deploy Gratuito Passo a Passo

Este guia vai ajudá-lo a colocar o vitaOS no ar de forma **100% gratuita**.

### Pré-requisitos

- Conta no [GitHub](https://github.com/signup) (grátis)
- Conta no [Vercel](https://vercel.com/signup) (grátis) - login com GitHub
- Conta no [Neon](https://neon.tech) (grátis) - banco PostgreSQL
- Conta no [OpenAI](https://platform.openai.com) ($18 créditos gratuitos)
- Conta no [Daily.co](https://daily.co) (grátis) - video calls

---

### Passo 1: Criar Contas nas Plataformas

#### 1.1 GitHub
1. Acesse [github.com](https://github.com)
2. Clique em "Sign up" e siga as instruções
3. Crie um novo repositório chamado `vitaos`

#### 1.2 Neon (Banco de Dados PostgreSQL)
1. Acesse [neon.tech](https://neon.tech)
2. Clique em "Sign up" e use login com GitHub
3. Clique em "New Project"
4. Nome: `vitaos-db`
5. Region: escolha a mais próxima de você
6. Clique em "Create Project"
7. Na aba "Connection Details", copie a **Connection string**

#### 1.3 OpenAI (IA)
1. Acesse [platform.openai.com](https://platform.openai.com)
2. Clique em "Sign up" e faça login
3. Vá para **Settings > API Keys**
4. Clique em **Create new secret key**
5. Copie a chave (começa com `sk-`)

#### 1.4 Daily.co (Video)
1. Acesse [daily.co](https://daily.co)
2. Clique em "Sign up" e use login com GitHub
3. Vá para **Settings > API Key**
4. Copie a API key

---

### Passo 2: Configurar no Computador

```bash
# Entre no diretório do projeto
cd vitaos

# Configure git
git config user.email "seu@email.com"
git config user.name "Seu Nome"

# Adicione o remote do GitHub (substitua SEU-USUARIO)
git remote add origin https://github.com/SEU-USUARIO/vitaos.git

# Commit inicial
git add .
git commit -m "Initial commit: vitaOS telemedicine platform"

# Push para GitHub
git branch -M main
git push -u origin main
```

---

### Passo 3: Deploy no Vercel

1. Acesse [vercel.com/dashboard](https://vercel.com/dashboard)
2. Clique em **"Add New..." > "Project"**
3. Selecione o repositório `vitaos` do seu GitHub
4. Clique em **"Import"**

#### Configurar Environment Variables:

Clique em **"Environment Variables"** e adicione:

| Variable | Value |
|----------|-------|
| `DATABASE_URL` | Cole a connection string do Neon |
| `NEXTAUTH_SECRET` | `vitaos-super-secret-key-2024-secure` |
| `NEXTAUTH_URL` | `https://vitaos.vercel.app` (ou seu domínio) |
| `OPENAI_API_KEY` | Cole sua chave da OpenAI |
| `DAILY_API_KEY` | Cole sua chave do Daily.co |

5. Clique em **"Deploy"**

Aguarde ~2 minutos para o deploy completar.

---

### Passo 4: Configurar o Banco de Dados

1. Acesse [neon.tech](https://neon.tech) > seu projeto
2. Vá para **SQL Editor**
3. O Prisma vai criar as tabelas automaticamente quando você rodar:
   ```bash
   # No seu computador (para desenvolvimento local)
   npx prisma db push
   ```

---

### Passo 5: Acessar o App

Após o deploy:
1. Acesse `https://vitaos.vercel.app` (ou o URL que o Vercel fornecer)
2. Cadastre-se como paciente ou médico
3. Comece a usar!

---

## 🛠️ Desenvolvimento Local

```bash
# Clone o repositório (se ainda não tiver)
git clone https://github.com/SEU-USUARIO/vitaos.git
cd vitaos

# Instale as dependências
npm install

# Configure as variáveis de ambiente
cp .env.example .env.local
# Edite .env.local com suas credenciais

# Configure o banco de dados
npx prisma generate
npx prisma db push

# Inicie o servidor
npm run dev

# Abra http://localhost:3000
```

---

## 📁 Estrutura do Projeto

```
vitaos/
├── prisma/
│   └── schema.prisma          # Schema do banco de dados
├── src/
│   ├── app/
│   │   ├── (auth)/           # Páginas de autenticação
│   │   │   ├── login/        # Login
│   │   │   └── register/     # Registro
│   │   ├── (main)/           # Páginas autenticadas
│   │   │   ├── dashboard/    # Dashboard principal
│   │   │   ├── appointments/ # Consultas
│   │   │   ├── doctors/      # Lista de médicos
│   │   │   ├── chat/         # Chat com IA
│   │   │   └── settings/     # Configurações
│   │   ├── (consultation)/   # Sala de consulta
│   │   │   └── room/[id]/    # Video call
│   │   └── api/              # API Routes
│   │       ├── auth/         # Autenticação
│   │       ├── doctors/      # Médicos
│   │       ├── appointments/ # Consultas
│   │       └── ai/           # Chat com IA
│   ├── components/
│   │   ├── ui/               # Componentes UI
│   │   ├── layout/           # Layout (Sidebar, Nav)
│   │   └── ...               # Outros componentes
│   ├── lib/
│   │   ├── db.ts             # Prisma client
│   │   ├── auth.ts           # Funções de auth
│   │   ├── ai.ts             # Integração OpenAI
│   │   └── utils.ts          # Utilitários
│   ├── store/                # Zustand stores
│   └── types/                # TypeScript types
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── README.md
```

---

## ✨ Funcionalidades

| Funcionalidade | Descrição |
|----------------|-----------|
| 🔐 **Autenticação** | Login/registro com email + social |
| 👨‍⚕️ **Perfil Médico** | CRM, especialidade, disponibilidade |
| 📅 **Agendamento** | Calendário inteligente, reminders |
| 📹 **Video Chamadas** | WebRTC HD com Daily.co |
| 🤖 **vitasAI** | Assistente de IA para triagem e suporte |
| 📋 **Prontuário** | Histórico médico digital |
| 💊 **Receitas** | Prescrições digitais com QR code |
| 📊 **Relatórios** | Estatísticas e insights |
| 🔒 **Segurança** | LGPD, criptografia, dados seguros |

---

## 🛡️ Segurança

- ✅ Criptografia de senhas (bcrypt)
- ✅ Tokens JWT com expiração
- ✅ HTTPS em todas as conexões
- ✅ Proteção CSRF
- ✅ Input sanitization
- ✅ Rate limiting (Upstash Redis)
- ✅ LGPD compliant

---

## 📝 Licença

MIT License - use livremente para projetos pessoais ou comerciais.

---

# 🇺🇸 English

## 🚀 Free Deployment Step by Step

This guide will help you deploy vitaOS for **100% free**.

### Prerequisites

- [GitHub](https://github.com/signup) account (free)
- [Vercel](https://vercel.com/signup) account (free) - sign up with GitHub
- [Neon](https://neon.tech) account (free) - PostgreSQL database
- [OpenAI](https://platform.openai.com) account ($18 free credits)
- [Daily.co](https://daily.co) account (free) - video calls

---

### Step 1: Create Accounts

#### 1.1 GitHub
1. Go to [github.com](https://github.com)
2. Click "Sign up" and follow instructions
3. Create a new repository called `vitaos`

#### 1.2 Neon (PostgreSQL Database)
1. Go to [neon.tech](https://neon.tech)
2. Click "Sign up" and use GitHub login
3. Click "New Project"
4. Name: `vitaos-db`
5. Region: choose closest to you
6. Click "Create Project"
7. In "Connection Details" tab, copy the **Connection string**

#### 1.3 OpenAI (AI)
1. Go to [platform.openai.com](https://platform.openai.com)
2. Click "Sign up" and log in
3. Go to **Settings > API Keys**
4. Click **Create new secret key**
5. Copy the key (starts with `sk-`)

#### 1.4 Daily.co (Video)
1. Go to [daily.co](https://daily.co)
2. Click "Sign up" and use GitHub login
3. Go to **Settings > API Key**
4. Copy the API key

---

### Step 2: Setup on Your Computer

```bash
# Enter the project directory
cd vitaos

# Configure git
git config user.email "your@email.com"
git config user.name "Your Name"

# Add GitHub remote (replace YOUR-USERNAME)
git remote add origin https://github.com/YOUR-USERNAME/vitaos.git

# Initial commit
git add .
git commit -m "Initial commit: vitaOS telemedicine platform"

# Push to GitHub
git branch -M main
git push -u origin main
```

---

### Step 3: Deploy to Vercel

1. Go to [vercel.com/dashboard](https://vercel.com/dashboard)
2. Click **"Add New..." > "Project"**
3. Select the `vitaos` repository from your GitHub
4. Click **"Import"**

#### Configure Environment Variables:

Click **"Environment Variables"** and add:

| Variable | Value |
|----------|-------|
| `DATABASE_URL` | Paste Neon connection string |
| `NEXTAUTH_SECRET` | `vitaos-super-secret-key-2024-secure` |
| `NEXTAUTH_URL` | `https://vitaos.vercel.app` (or your domain) |
| `OPENAI_API_KEY` | Paste your OpenAI key |
| `DAILY_API_KEY` | Paste your Daily.co key |

5. Click **"Deploy"**

Wait ~2 minutes for deployment to complete.

---

### Step 4: Access the App

After deployment:
1. Go to `https://vitaos.vercel.app` (or the URL Vercel provides)
2. Sign up as patient or doctor
3. Start using it!

---

## 🛠️ Local Development

```bash
# Clone the repository (if you don't have it)
git clone https://github.com/YOUR-USERNAME/vitaos.git
cd vitaos

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env.local
# Edit .env.local with your credentials

# Setup database
npx prisma generate
npx prisma db push

# Start server
npm run dev

# Open http://localhost:3000
```

---

## 📁 Project Structure

```
vitaos/
├── prisma/
│   └── schema.prisma          # Database schema
├── src/
│   ├── app/
│   │   ├── (auth)/           # Auth pages
│   │   │   ├── login/        # Login
│   │   │   └── register/     # Register
│   │   ├── (main)/           # Authenticated pages
│   │   │   ├── dashboard/    # Main dashboard
│   │   │   ├── appointments/ # Appointments
│   │   │   ├── doctors/      # Doctor list
│   │   │   ├── chat/         # AI chat
│   │   │   └── settings/     # Settings
│   │   ├── (consultation)/   # Consultation room
│   │   │   └── room/[id]/    # Video call
│   │   └── api/              # API Routes
│   │       ├── auth/         # Authentication
│   │       ├── doctors/      # Doctors
│   │       ├── appointments/ # Appointments
│   │       └── ai/           # AI chat
│   ├── components/
│   │   ├── ui/               # UI components
│   │   ├── layout/           # Layout (Sidebar, Nav)
│   │   └── ...               # Other components
│   ├── lib/
│   │   ├── db.ts             # Prisma client
│   │   ├── auth.ts           # Auth functions
│   │   ├── ai.ts             # OpenAI integration
│   │   └── utils.ts          # Utilities
│   ├── store/                # Zustand stores
│   └── types/                # TypeScript types
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── README.md
```

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔐 **Authentication** | Email + social login |
| 👨‍⚕️ **Doctor Profile** | CRM, specialty, availability |
| 📅 **Scheduling** | Smart calendar, reminders |
| 📹 **Video Calls** | WebRTC HD with Daily.co |
| 🤖 **vitasAI** | AI assistant for triage and support |
| 📋 **Medical Records** | Digital health history |
| 💊 **Prescriptions** | Digital prescriptions with QR code |
| 📊 **Reports** | Statistics and insights |
| 🔒 **Security** | GDPR compliant, encrypted, safe |

---

## 🛡️ Security

- ✅ Password encryption (bcrypt)
- ✅ JWT tokens with expiration
- ✅ HTTPS on all connections
- ✅ CSRF protection
- ✅ Input sanitization
- ✅ Rate limiting (Upstash Redis)
- ✅ GDPR compliant

---

## 📝 License

MIT License - free for personal or commercial projects.

---

<p align="center">
  <strong>Made with ❤️ for healthcare</strong>
  <br />
  vitaOS - Intelligent Telemedicine Platform
</p>