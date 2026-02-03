# PAWG - Portal de Administração e Workflow de Guias

Sistema de gestão tributária municipal para controle de licenças e contribuintes.

## 🚀 Funcionalidades
- Cadastro de contribuintes (CNPJ/CPF)
- Cálculo automático de TFLF, ISSQN e VISA
- Consulta automática de CNPJ via API
- Pesquisa de faltas de pagamento
- Importação de dados via TXT
- Exportação para CSV

## 🔧 Tecnologias
- React 18
- Firebase (Realtime Database + Auth)
- TailwindCSS
- API CNPJA

## ⚙️ Configuração
1. Configure Firebase em `firebaseConfig`
2. Adicione regras de segurança no Realtime Database
3. Crie usuários no Firebase Authentication

## 📝 Desenvolvedor
Elvis Ferreira - elvis.fdj@aol.com
```

### 2. **.gitignore** - Proteger dados sensíveis
```
# Configurações locais
.env
.env.local

# Logs
*.log

# Sistema
.DS_Store
Thumbs.db

# Backup
*.backup
*.bak
