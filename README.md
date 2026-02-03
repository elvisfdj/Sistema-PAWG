# 💻 PAWG – Portal de Administração e Workflow de Guias

Sistema completo de gestão tributária municipal para controle de licenças, contribuintes e arrecadação.

![Status](https://img.shields.io/badge/status-ativo-brightgreen) ![Versão](https://img.shields.io/badge/vers%C3%A3o-2.0-blue) ![Firebase](https://img.shields.io/badge/Firebase-Realtime%20DB-orange)

---

## 🎯 **Funcionalidades Principais**

### 📋 **Gestão de Contribuintes**
- ✅ Cadastro de CNPJ e CPF
- ✅ Consulta automática de CNPJ via API CNPJA
- ✅ Importação em massa via arquivo TXT
- ✅ Detecção automática de duplicidades
- ✅ Marcadores coloridos para organização

### 💰 **Cálculos Tributários Automáticos**
- ✅ TFLF (Taxa de Fiscalização de Licença e Funcionamento)
- ✅ ISSQN (Imposto Sobre Serviços)
- ✅ Taxa de Vigilância Sanitária (VISA)
- ✅ Tabela progressiva baseada em área (m²)
- ✅ Suporte a diferentes regimes tributários

### 🔍 **Pesquisa e Análise**
- ✅ Pesquisa de faltas de pagamento por período
- ✅ Filtros avançados (auditor, situação, tributação)
- ✅ Busca por nome, documento ou inscrição
- ✅ Ordenação por colunas
- ✅ Visualização por abas (Principal, MEI, Autônomo, VISA)

### 💾 **Backup e Exportação**
- ✅ Backup completo em JSON
- ✅ Restauração de backup
- ✅ Exportação para CSV
- ✅ Todos os dados locais (sem custos Firebase)

### 📊 **Dashboard e Estatísticas**
- ✅ Total de contribuintes
- ✅ Pendentes de lançamento
- ✅ CNPJs verificados
- ✅ Arrecadação total (TFLF, ISSQN, VISA)
- ✅ Documentos duplicados

---

## 🚀 **Tecnologias Utilizadas**

| Tecnologia | Descrição |
|-----------|-----------|
| **React 18** | Interface responsiva e interativa |
| **Firebase Realtime Database** | Banco de dados em tempo real |
| **Firebase Authentication** | Autenticação segura de usuários |
| **TailwindCSS** | Estilização moderna e responsiva |
| **API CNPJA** | Consulta automática de dados empresariais |
| **Twemoji** | Emojis consistentes em todos os sistemas |

---

## ⚙️ **Configuração e Instalação**

### 1️⃣ **Clone o Repositório**
```bash
git clone https://github.com/seu-usuario/pawg.git
cd pawg
```

### 2️⃣ **Configure o Firebase**

No arquivo `index.html`, localize e configure suas credenciais Firebase:

```javascript
const firebaseConfig = {
    apiKey: "SUA_API_KEY",
    authDomain: "SEU_PROJETO.firebaseapp.com",
    databaseURL: "https://SEU_PROJETO.firebaseio.com/",
    projectId: "SEU_PROJETO",
    storageBucket: "SEU_PROJETO.firebasestorage.app",
    messagingSenderId: "SEU_ID",
    appId: "SEU_APP_ID"
};
```

### 3️⃣ **Configure as Regras do Firebase Realtime Database**

No Firebase Console → Realtime Database → Regras:

```json
{
  "rules": {
    "documentos": {
      ".read": "auth != null",
      ".write": "auth != null"
    },
    "contribuintes": {
      ".read": "auth != null",
      ".write": "auth != null"
    },
    "faltas": {
      ".read": "auth != null",
      ".write": "auth != null"
    }
  }
}
```

### 4️⃣ **Crie Usuários no Firebase Authentication**

Firebase Console → Authentication → Adicionar usuário

### 5️⃣ **Abra o Sistema**

Basta abrir o arquivo `index.html` no navegador ou hospedar no Firebase Hosting.

---

## 📖 **Como Usar**

### **Login**
1. Acesse o sistema
2. Faça login com email e senha cadastrados no Firebase

### **Cadastro de Contribuintes**
- **Opção 1:** Clique em "➕ Inserir" para cadastro manual
- **Opção 2:** Use "📁 Importar TXT" para importação em massa

### **Consulta de CNPJ**
- Clique em 🔍 ao lado do contribuinte
- Ou use "🔍 Consultar CNPJs" para consultar todos de uma vez

### **Pesquisa de Faltas**
1. Configure o intervalo de inscrições municipais
2. Clique em "🕵️ Consultar Faltas"
3. Veja os resultados na aba "📢 Faltas"

### **Filtros Avançados**
- Use o painel "🔍 Filtros Avançados"
- Combine múltiplos filtros
- Clique em "🗑️ Limpar" para resetar

### **Backup e Restauração**
- **Backup:** Clique em "💾 Backup" para baixar JSON
- **Restauração:** Clique em "📥 Restaurar" e selecione o arquivo JSON

---

## 📂 **Estrutura do Projeto**

```
pawg/
├── index.html              # Aplicação completa (React + Firebase)
├── README.md               # Este arquivo
└── backup/                 # Pasta para backups (não versionada)
```

---

## 💡 **Dicas de Uso**

### **Performance**
- ✅ Use filtros para navegar em listas grandes
- ✅ Consulte CNPJs em lote fora do horário de pico
- ✅ Faça backup regularmente (recomendado: mensal)

### **Segurança**
- ✅ Nunca compartilhe suas credenciais do Firebase
- ✅ Use senhas fortes para usuários
- ✅ Mantenha backups em local seguro

### **Limites do Firebase (Plano Gratuito)**
- 💾 1GB de armazenamento
- 🌐 10GB de transferência/mês
- 👥 10.000 usuários simultâneos

---

## 🆘 **Solução de Problemas**

| Problema | Solução |
|----------|---------|
| **Erro de permissão no Firebase** | Verifique as regras do Realtime Database |
| **Consulta CNPJ não funciona** | API tem limite de 3 consultas/minuto |
| **Dados não salvam** | Verifique conexão com internet e regras Firebase |
| **Emojis aparecem diferentes** | Twemoji está carregando? Verifique console |

---

## 📊 **Atualizações e Melhorias**

### **Versão 2.0** (Atual)
- ✅ Filtros avançados
- ✅ Backup/Restauração local
- ✅ Twemoji para emojis consistentes
- ✅ Interface de pesquisa de faltas
- ✅ Correção de duplicações no código

### **Versão 1.0**
- ✅ Sistema básico de cadastro
- ✅ Cálculos tributários
- ✅ Consulta API CNPJA
- ✅ Exportação CSV

---

## 👨‍💻 **Desenvolvedor**

**Elvis Ferreira**
- 📧 Email: elvis.fdj@aol.com
- 📱 WhatsApp: (22) 98138-2619

---

## 📄 **Licença**

Este projeto é de uso interno para gestão municipal. Todos os direitos reservados.

---

## 🙏 **Agradecimentos**

- Firebase pela infraestrutura gratuita
- CNPJA pela API de consulta de CNPJs
- Twitter pelo Twemoji
- Comunidade React por todo o suporte

---

**🎯 Sistema desenvolvido com foco em praticidade, segurança e eficiência!**
