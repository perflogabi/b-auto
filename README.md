# B-Auto - Sistema de Chat Automatizado

Sistema de chat automatizado com interface similar ao WhatsApp, desenvolvido para fornecer atendimento ao cliente através de integração com automações n8n e processamento de mensagens via IA.

## 📋 Sobre o Projeto

O **B-Auto** é uma aplicação web moderna que permite aos usuários iniciarem conversas automatizadas com um assistente virtual. O sistema oferece uma experiência de chat intuitiva e familiar, com interface inspirada no WhatsApp, permitindo que empresas ofereçam atendimento automatizado 24/7 aos seus clientes.

### Funcionalidades Principais

- 💬 **Interface de Chat Moderna**: Interface responsiva com design inspirado no WhatsApp
- 🤖 **Integração com n8n**: Processamento de mensagens através de automações n8n
- 📱 **Gestão de Sessões**: Sistema de sessões persistentes com armazenamento local
- 🔄 **Polling Inteligente**: Verificação automática de respostas do assistente
- 📝 **Validação de Formulário**: Validação de nome e telefone no formulário inicial
- 💾 **Armazenamento Local**: Persistência de mensagens e sessões no navegador
- ⚡ **Tempo Real**: Atualização em tempo real do status das mensagens

## 🛠️ Tecnologias Utilizadas

- **Next.js 16.1.1** - Framework React para produção
- **React 19.2.3** - Biblioteca JavaScript para interfaces
- **TypeScript 5** - Tipagem estática para JavaScript
- **Tailwind CSS 4** - Framework CSS utilitário
- **TanStack Query (React Query) 5** - Gerenciamento de estado do servidor
- **React Icons** - Biblioteca de ícones
- **UUID** - Geração de identificadores únicos

## 📁 Estrutura do Projeto

```
b-auto/
├── src/
│   ├── app/
│   │   ├── api/
│   │   │   ├── chat/
│   │   │   │   ├── route.ts          # Endpoint para envio de mensagens
│   │   │   │   └── status/
│   │   │   │       └── route.ts      # Endpoint para verificar status de respostas
│   │   │   └── webhook/
│   │   │       └── n8n/
│   │   │           └── route.ts      # Webhook para receber respostas do n8n
│   │   ├── autochat/
│   │   │   ├── _components/
│   │   │   │   └── chat/
│   │   │   │       ├── ChatInterface.tsx  # Interface principal do chat
│   │   │   │       ├── ChatInput.tsx      # Componente de input de mensagens
│   │   │   │       ├── MessageBubble.tsx  # Componente de bolha de mensagem
│   │   │   │       └── WelcomeForm.tsx    # Formulário de boas-vindas
│   │   │   └── page.tsx              # Página principal do autochat
│   │   └── page.tsx                  # Página inicial (redireciona para /autochat)
│   ├── components/
│   │   └── providers/
│   │       └── QueryProvider.tsx     # Provider do React Query
│   ├── lib/
│   │   ├── actions/
│   │   │   └── chat-actions.ts       # Server actions para chat
│   │   ├── api/
│   │   │   └── response-store.ts    # Armazenamento temporário de respostas
│   │   ├── storage/
│   │   │   ├── chat-storage.ts      # Gerenciamento de mensagens
│   │   │   └── session.ts           # Gerenciamento de sessões
│   │   └── types/
│   │       └── chat.ts              # Tipos TypeScript para chat
│   └── utils/
│       └── formater.ts              # Utilitários de formatação (telefone)
└── package.json
```

## 🚀 Como Executar

### Pré-requisitos

- Node.js 18+ instalado
- npm, yarn, pnpm ou bun

### Instalação

1. Clone o repositório:
```bash
git clone <url-do-repositorio>
cd b-auto
```

2. Instale as dependências:
```bash
npm install
# ou
yarn install
# ou
pnpm install
```

3. Configure as variáveis de ambiente (crie um arquivo `.env.local`):
```env
N8N_WEBHOOK_URL=https://seu-webhook-n8n.com/webhook
NEXT_PUBLIC_APP_URL=http://localhost:3000
NEXT_PUBLIC_NAME=Nome da Empresa
```

4. Execute o servidor de desenvolvimento:
```bash
npm run dev
# ou
yarn dev
# ou
pnpm dev
# ou
bun dev
```

5. Abra [http://localhost:3000](http://localhost:3000) no navegador.

## 🔧 Variáveis de Ambiente

| Variável | Descrição | Obrigatória |
|----------|-----------|-------------|
| `N8N_WEBHOOK_URL` | URL do webhook do n8n para processar mensagens | Não (usa mock se não configurada) |
| `NEXT_PUBLIC_APP_URL` | URL base da aplicação | Não (padrão: http://localhost:3000) |
| `NEXT_PUBLIC_NAME` | Nome da empresa exibido no chat | Não |

## 🔄 Fluxo de Funcionamento

1. **Inicialização**: Usuário acessa a aplicação e preenche o formulário com nome e telefone
2. **Criação de Sessão**: Sistema cria uma sessão única e armazena localmente
3. **Envio de Mensagem**: Usuário envia mensagem → API `/api/chat` recebe e envia para n8n
4. **Processamento**: n8n processa a mensagem (possivelmente com IA) e gera resposta
5. **Webhook**: n8n envia resposta para `/api/webhook/n8n`
6. **Polling**: Interface verifica periodicamente se há resposta disponível via `/api/chat/status`
7. **Exibição**: Resposta é exibida na interface do chat

## 📝 Scripts Disponíveis

- `npm run dev` - Inicia o servidor de desenvolvimento
- `npm run build` - Cria build de produção
- `npm run start` - Inicia o servidor de produção
- `npm run lint` - Executa o linter ESLint

## 🎨 Características da Interface

- Design inspirado no WhatsApp com cores e layout familiares
- Indicador de status online/offline
- Bolhas de mensagem diferenciadas para usuário e assistente
- Status de mensagens (enviando, enviada, entregue, erro)
- Scroll automático para novas mensagens
- Formatação automática de telefone brasileiro
- Validação de formulário em tempo real

## 🔐 Armazenamento

O sistema utiliza `localStorage` do navegador para:
- Armazenar sessões de chat
- Persistir histórico de mensagens
- Manter dados do usuário (nome e telefone)

## 📚 Documentação Adicional

- [Next.js Documentation](https://nextjs.org/docs)
- [React Query Documentation](https://tanstack.com/query/latest)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [n8n Documentation](https://docs.n8n.io/)

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests.

## 📄 Licença

Este projeto é privado.
