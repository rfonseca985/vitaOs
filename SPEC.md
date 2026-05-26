# vitaOS - Plataforma de Telemedicina Inteligente

## 1. Conceito & Visão

**vitaOS** é uma plataforma de telemedicina completa que conecta médicos e pacientes de forma segura, eficiente e inteligente. A plataforma elimina barreiras geográficas e temporais, permitindo consultas médicas online com IA integrada para triagem, assistência diagnóstica e acompanhamento remoto.

**Missão:** Democratizar o acesso à saúde de qualidade através da tecnologia, facilitando conexões entre profissionais de saúde e pacientes em qualquer lugar do mundo.

**Feeling:** Profissional, confiável, acolhedor, moderno e seguro. A sensação deve transmitir que vidas estão em boas mãos.

---

## 2. Design Language

### Aesthetic Direction
Healthcare premium design - inspirado em apps como Teladoc, Doctolib e plataformas bancárias de alto nível. Clean, espaçoso, com toques de azul médico transmitindo confiança e verde saúde transmitindo bem-estar.

### Color Palette

| Cor | Hex | Uso |
|-----|-----|-----|
| **Primary Blue** | `#2563EB` | Ações principais, links, elementos de confiança médica |
| **Primary Dark** | `#1D4ED8` | Hover states |
| **Secondary Green** | `#10B981` | Sucesso, saúde, bem-estar |
| **Accent Purple** | `#7C3AED` | IA, recursos inteligentes |
| **Warning Amber** | `#F59E0B` | Alertas, atenção |
| **Error Red** | `#EF4444` | Erros, urgências |
| **Background** | `#F8FAFC` | Fundo principal |
| **Surface** | `#FFFFFF` | Cards, modais |
| **Text Primary** | `#0F172A` | Títulos |
| **Text Secondary** | `#64748B` | Descrições |

### Typography

- **Headings:** Inter (700, 600) - clean, professional
- **Body:** Inter (400, 500) - legibilidade máxima
- **Medical Data:** JetBrains Mono (números, códigos)
- **AI Responses:** Sistema de rating visual com emojis

### Spatial System

- Base unit: 4px
- Spacing scale: 4, 8, 12, 16, 24, 32, 48, 64px
- Border radius: 8px (buttons), 12px (cards), 16px (modals)
- Shadow: `0 1px 3px rgba(0,0,0,0.1)` (subtle), `0 10px 40px rgba(0,0,0,0.15)` (elevated)

### Motion Philosophy

- **Entrances:** Fade-in 300ms ease-out + slide-up 8px
- **Transitions:** 200ms ease-in-out for state changes
- **Loading:** Pulse animation for skeleton states
- **Video:** Smooth connection indicators
- **AI:** Typewriter effect for AI responses, sparkle animations

---

## 3. Layout & Structure

### Information Architecture

```
├── Landing (não logado)
│   ├── Hero com CTA
│   ├── Features principais
│   ├── Especialidades médicas
│   ├── Como funciona
│   ├── Depoimentos
│   └── FAQ
│
├── Auth
│   ├── Login (email/social)
│   ├── Registro
│   └── Recuperação de senha
│
├── Paciente Dashboard
│   ├── Visão geral (próximas consultas, resumo saúde)
│   ├── Consultas (agendar, gerenciar, histórico)
│   ├── Chat com IA (triagem sintomática)
│   ├── Prontuário (histórico médico)
│   ├── Receita e exames
│   └── Configurações
│
├── Médico Dashboard
│   ├── Agenda (calendário, disponibilidade)
│   ├── Pacientes (lista, prontuário)
│   ├── Consultas (ativas, histórico)
│   ├── Chat com IA (auxílio diagnóstico)
│   ├── Prescrições
│   └── Configurações
│
├── Sala de Consulta
│   ├── Video call (principal)
│   ├── Chat lateral
│   ├── Prontuário rápido
│   ├── Prescrição integrada
│   └── Notas médicas
│
└── Admin (se aplicável)
    └── Gerenciamento de plataforma
```

### Navigation

- **Desktop:** Sidebar fixa esquerda (240px)
- **Mobile:** Bottom tab bar (5 items principais) + hamburger menu
- **Responsive breakpoints:** 640px (sm), 768px (md), 1024px (lg), 1280px (xl)

---

## 4. Features & Interactions

### 4.1 Autenticação

**Login:**
- Email + senha com validação inline
- "Lembrar-me" com cookie persistente
- Recuperação de senha via email
- Login social: Google, Microsoft

**Registro:**
- Multi-step: Dados pessoais → Tipo de conta (Paciente/Médico) → Verificação
- Paciente: nome, email, senha, data nascimento, CPF, telefone
- Médico: campos do paciente + CRM, especialidade, comprovante

**Sessão:**
- JWT tokens com refresh
- Tempo de expiração: 7 dias (lembrar), 24h (normal)
- Logout automático em inatividade (30min)

### 4.2 Agendamento de Consultas

**Para Pacientes:**
- Browsing de médicos por especialidade
- Filtros: disponibilidade, avaliação, preço
- Seleção de horário disponível (calendário visual)
- Confirmação com lembretes por email/SMS
- Pagamento integrado (se aplicável)

**Para Médicos:**
- Definir disponibilidade semanal
- Bloquear horários específicos
- Definir valores de consulta
- Aceitar/rejeitar solicitações
- Configurar tempo de consulta (15/30/45/60min)

### 4.3 Video Consulta

**Conexão:**
- WebRTC para video/audio em tempo real
- Quality indicator (excelente/bom/regular/ruim)
- Reconnection automática em quedas
- fallback para áudio apenas se vídeo falhar

**Durante Consulta:**
- Toggle video on/off
- Toggle microphone on/off
- Screen sharing (médico pode compartilhar tela)
- Chat em tempo real (lado direito)
- Timer de duração da consulta
- Botão "Encerrar consulta" com confirmação

**Pós-Consulta:**
- Avaliação da consulta (1-5 estrelas)
- Comentário opcional
- Paciente recebe resumo por email

### 4.4 Chat com IA (vitaAI)

**Para Pacientes:**
- Triagem de sintomas (árvore de decisão)
- Respostas a perguntas frequentes de saúde
- Agendamento assistido
- Lembretes de medicação
- Acompanhamento pós-consulta

**Para Médicos:**
- Auxílio diagnóstico (sintomas → possíveis condições)
- Sugestões de exames
- Informações sobre medicamentos
- Busca de protocolos clínicos
- Tradução de termos médicos

**Interface:**
- Chat conversacional com avatar da IA
- Indicador de "digitando..."
- Encadeamento de perguntas para refinamento
- Botões de ação rápida
- Disclaimer de que é assistente e não substitui médico

### 4.5 Prontuário Eletrônico

**Paciente:**
- Dados pessoais e histórico
- Alergias e condições crônicas
- Medicamentos em uso
- Histórico de consultas e diagnósticos
- Resultados de exames (upload PDF)
- Vacinas registradas

**Médico:**
- Acesso ao prontuário durante consulta
- Adicionar notas e diagnósticos
- Prescrever medicamentos
- Solicitar exames
- Gerar relatório da consulta

### 4.6 Prescrição Digital

- Lista de medicamentos com posologia
- Instruções de uso
- Validade da receita (30 dias padrão)
- QR code para verificação de autenticidade
- Envio por email ao paciente

---

## 5. Component Inventory

### Auth Components

**LoginForm:**
- States: default, loading, error, success
- Email input com validação
- Password input com toggle visibility
- Submit button com loading spinner
- Link para registro e recuperação

**RegisterForm:**
- States: step 1, step 2, step 3, loading, error
- Progress indicator (steps)
- Form validation inline
- File upload para médicos (comprovante CRM)

### Navigation Components

**Sidebar (Desktop):**
- Logo no topo
- Navigation items com ícones e labels
- Active state: background highlight + border-left
- User avatar e dropdown no footer
- Collapse toggle

**BottomNav (Mobile):**
- 5 tabs: Home, Consultas, Chat IA, Agenda, Perfil
- Active state: filled icon + label
- Badge para notificações

### Medical Components

**DoctorCard:**
- Avatar, nome, especialidade, CRM
- Rating (estrelas) + número de avaliações
- Preço da consulta
- Disponibilidade (próximo horário livre)
- Botão "Agendar"

**AppointmentCard:**
- Data e horário
- Status: agendada, em andamento, concluída, cancelada
- Doctor/Patient info
- Ações: entrar, remarcar, cancelar

**VideoRoom:**
- Video principal (fullscreen ou picture-in-picture)
- Controles: mute, camera, screen share, chat, end
- Indicadores de qualidade
- Chat panel (toggle)
- Timer e info da consulta

**ChatBubble:**
- Avatar do remetente
- Mensagem com timestamp
- Status: enviado, entregue, lido
- AI indicator (sparkle icon)

### AI Components

**AIAssistant:**
- Header com avatar e nome "vitaAI"
- Message history com scroll
- Input com send button
- Suggested actions como chips
- Typing indicator animado

**SymptomChecker:**
- Multi-step form wizard
- Progress bar
- perguntas com botões de resposta
- Summary no final com ações recomendadas

---

## 6. Technical Approach

### Stack

| Layer | Technology |
|-------|------------|
| **Framework** | Next.js 14 (App Router) |
| **Language** | TypeScript |
| **Database** | PostgreSQL (Neon free tier) |
| **ORM** | Prisma |
| **Auth** | NextAuth.js + JWT |
| **Real-time** | Socket.io |
| **Video** | Daily.co / Jitsi (free tier) |
| **AI** | OpenAI API (GPT-4) |
| **Styling** | Tailwind CSS |
| **State** | React Context + Zustand |
| **Forms** | React Hook Form + Zod |
| **Icons** | Lucide React |

### Database Schema

```
User
├── id (cuid)
├── email (unique)
├── password (hashed)
├── role (PATIENT | DOCTOR | ADMIN)
├── name
├── phone
├── dateOfBirth
├── cpf
├── avatar
├── createdAt
├── updatedAt
│
Doctor (extensão de User)
├── id
├── userId
├── crm (unique)
├── specialty
├── specialtyId
├── bio
├── consultationPrice
├── consultationDuration (default 30)
├── availability (JSON)
├── rating (float)
├── reviewCount
│
Patient (extensão de User)
├── id
├── userId
├── emergencyContact
├── allergies (JSON)
├── conditions (JSON)
├── medications (JSON)
│
Appointment
├── id
├── patientId
├── doctorId
├── scheduledAt
├── duration
├── status (SCHEDULED | IN_PROGRESS | COMPLETED | CANCELLED)
├── type (VIDEO | CHAT | PHONE)
├── notes
├── createdAt
│
Message
├── id
├── conversationId
├── senderId
├── content
├── type (TEXT | IMAGE | FILE)
├── createdAt
│
Prescription
├── id
├── appointmentId
├── doctorId
├── patientId
├── medications (JSON)
├── instructions
├── validUntil
├── qrCode
│
MedicalRecord
├── id
├── patientId
├── doctorId
├── appointmentId (nullable)
├── type (NOTE | DIAGNOSIS | EXAM_RESULT | VACCINE)
├── title
├── content
├── attachments (JSON)
├── createdAt
│
Conversation (AI Chat)
├── id
├── userId
├── messages (JSON)
├── context (JSON)
├── createdAt
├── updatedAt
```

### API Design

```
AUTH
POST   /api/auth/register     - Criar conta
POST   /api/auth/login        - Login
POST   /api/auth/logout       - Logout
GET    /api/auth/me           - Dados do usuário

USERS
GET    /api/users/:id         - Perfil público
PUT    /api/users/:id         - Atualizar perfil
GET    /api/doctors           - Lista de médicos (com filtros)
GET    /api/doctors/:id       - Detalhes do médico

APPOINTMENTS
GET    /api/appointments      - Minhas consultas
POST   /api/appointments      - Criar agendamento
PUT    /api/appointments/:id  - Atualizar consulta
DELETE /api/appointments/:id  - Cancelar consulta
POST   /api/appointments/:id/join - Entrar na sala

MESSAGES
GET    /api/messages/:conversationId - Mensagens da conversa
POST   /api/messages            - Enviar mensagem

AI (vitaAI)
POST   /api/ai/chat             - Chat com IA
POST   /api/ai/symptoms         - Triagem de sintomas
POST   /api/ai/diagnosis        - Auxílio diagnóstico

MEDICAL RECORDS
GET    /api/records             - Prontuário do paciente
POST   /api/records             - Criar registro médico

PRESCRIPTIONS
GET    /api/prescriptions       - Minhas prescrições
POST   /api/prescriptions       - Criar prescrição (médico)
```

### Security

- HTTPS em todas as conexões
- JWT tokens com expiração
- CSRF protection
- Rate limiting
- Input sanitization
- CORS configurado
- Helmet.js para headers de segurança
- Banco de dados com encryption at rest

### Deployment Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     VERCEL (Frontend)                    │
│                   Next.js 14 App Router                  │
└─────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────┐
│                    NEON (Database)                       │
│                  PostgreSQL (Free Tier)                  │
│               0.5GB storage, 1 project                   │
└─────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────┐
│                    UPSTASH (Redis)                       │
│              Rate limiting & caching                     │
│                 Serverless kv store                      │
└─────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────┐
│                    OPENAI (AI)                           │
│              GPT-4 para vitaAI Assistant                 │
│                 $18 credits free                         │
└─────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────┐
│                   DAILY.CO (Video)                       │
│            WebRTC infrastructure                         │
│             Free: 10K mins/month                         │
└─────────────────────────────────────────────────────────┘
```

---

## 7. Content & Copy

### Landing Page

**Hero:**
- "Saúde ao alcance de todos, em qualquer lugar."
- "Consultas médicas online com médicos qualificados. Sem filas, sem deslocamento, com IA integrada."

**Features:**
- "Video Consultas HD" - Conecte-se com seu médico por video em alta qualidade
- "IA Assistente" - vitasAI ajuda na triagem e acompanhamento
- "Prontuário Digital" - Seu histórico médico sempre acessível
- "Prescrições Digitais" - Receitas válidas emitidas durante a consulta

### Error Messages

- "Ops! Algo deu errado. Por favor, tente novamente."
- "Conexão instável. Verifique sua internet."
- "Sessão expirada. Por favor, faça login novamente."

### AI Assistant (vitaAI)

- "Olá! Sou a vitasAI, sua assistente de saúde. Como posso ajudar?"
- "Entendi seus sintomas. Vou preparar algumas informações para você."
- "⚠️ Lembre-se: sou uma assistente e não substituo advice médico profissional."

---

## 8. Free Deployment Guide

### Passo 1: Criar Contas Gratuitas

1. **GitHub** (se não tiver)
   - https://github.com/signup
   - FREE plano é suficiente

2. **Vercel** (Hosting)
   - https://vercel.com/signup
   - Login com GitHub (grátis)

3. **Neon** (Database PostgreSQL)
   - https://neon.tech
   - Login com GitHub (grátis)
   - Criar projeto: "vitaos-db"
   - Copiar connection string

4. **Upstash** (Redis para cache)
   - https://upstash.com
   - Login com GitHub (grátis)
   - Criar Redis database
   - Copiar REST URL e Token

5. **OpenAI** (AI)
   - https://platform.openai.com
   - Login com conta Google/Microsoft
   - $18 free credits inclusos
   - Criar API key em Settings > API Keys

6. **Daily.co** (Video)
   - https://daily.co
   - Login com GitHub (grátis)
   - Free tier: 10.000 minutos/mês
   - Criar API key

### Passo 2: Configurar Repositório

```bash
# No terminal do seu computador
cd vitaos

# Adicionar remote do GitHub
git remote add origin https://github.com/SEU-USERNAME/vitaos.git

# Fazer commit inicial
git add .
git commit -m "Initial commit: vitaOS telemedicine platform"

# Push para GitHub
git branch -M main
git push -u origin main
```

### Passo 3: Deploy no Vercel

1. Acesse https://vercel.com/dashboard
2. Clique "New Project"
3. Selecione repositório "vitaos" do GitHub
4. Configure Environment Variables:

```
DATABASE_URL=postgresql://user:password@host/database?sslmode=require
NEXTAUTH_SECRET=generate-random-32-char-string
NEXTAUTH_URL=https://vitaos.vercel.app
OPENAI_API_KEY=sk-...
DAILY_API_KEY=...
UPSTASH_REDIS_REST_URL=https://...
UPSTASH_REDIS_REST_TOKEN=...
```

5. Clique "Deploy"

### Passo 4: Configurar Database

1. No Neon Console, vá para Query Editor
2. Execute o schema SQL (será gerado pelo Prisma)

```sql
-- O Prisma vai criar isso automaticamente
-- Execute: npx prisma db push
```

### Passo 5: Configurar DNS (Opcional)

Para domínio personalizado:
1. Compre domínio (ex: namecheap.com, ~$12/ano)
2. No Vercel > Domains > Add
3. Configure DNS do registrador:
   - A record: @ → 76.76.21.21
   - CNAME: www → cname.vercel-dns.com

---

## 9. Running Locally

### Pré-requisitos
- Node.js 18+
- npm ou yarn
- Conta no Neon (grátis)
- Conta no OpenAI (grátis)

### Instalação

```bash
# Clone ou entre no diretório
cd vitaos

# Instale dependências
npm install

# Configure variáveis de ambiente
cp .env.example .env.local
# Edite .env.local com suas credenciais

# Configure banco de dados
npx prisma generate
npx prisma db push

# Inicie desenvolvimento
npm run dev

# Abra http://localhost:3000
```

---

## 10. Maintenance & Monitoring

### Logs
- Vercel Dashboard > Functions > Logs
- Erros e warnings em tempo real

### Métricas
- Vercel Analytics (built-in, free)
- Neon dashboard para performance do DB
- Daily.co para métricas de video

### Updates
```bash
# Atualizar código
git add . && git commit -m "fix: ..."

# Push会自动触发deploy
git push
```

---

*Documento criado para fins profissionais. Todos os recursos médicos são informativos e não substituem advice profissional. Sempre consulte um médico qualificado para decisões médicas.*