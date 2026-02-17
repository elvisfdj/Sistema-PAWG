# 💻 PAWG – Portal de Administração e Workflow de Guias

Sistema web completo para gestão de contribuintes, lançamento de taxas municipais (TFLF, ISSQN, VISA) e controle de documentos administrativos.

![Status](https://img.shields.io/badge/status-ativo-success)
![Versão](https://img.shields.io/badge/versão-2.0-blue)
![Licença](https://img.shields.io/badge/licença-MIT-green)

---

## 📋 Sobre o Sistema

O **PAWG** é uma solução desenvolvida para automatizar e otimizar processos de fiscalização tributária municipal, oferecendo:

- 📊 **Gestão de Contribuintes**: Cadastro, importação em lote e consulta automatizada via API CNPJ
- 💰 **Cálculo de Taxas**: TFLF (Taxa de Fiscalização e Localização), ISSQN (Imposto Sobre Serviços) e Vigilância Sanitária
- 🏥 **Classificação VISA**: Identificação automática de CNAEs sujeitos à vigilância sanitária
- 📁 **Controle Documental**: Gestão de editais, ofícios, memorandos e outros documentos
- 📈 **Dashboards**: Indicadores em tempo real de arrecadação, pendências e duplicidades
- 🔄 **Reprocessamento**: Atualização em lote de dados via API

---

## ✨ Principais Funcionalidades

### 🎯 Módulo Contribuintes

- ✅ **Importação TXT**: Upload de arquivos com múltiplos contribuintes
- 🔍 **Consulta CNPJ Automática**: Integração com API open.cnpja.com
- 🏢 **Classificação Inteligente**:
  - Porte (ME/EPP/DEMAIS)
  - Tributação (MEI/SIMPLES/LUCRO PRESUMIDO/AUTÔNOMO)
  - Necessidade de licença VISA (baseada em CNAEs)
- 📋 **Gestão Individual**: Inserção manual, edição inline e exclusão
- 🔄 **Reprocessamento em Lote**: Atualização de dados de CNPJs verificados
- 🎨 **Marcadores Coloridos**: Organização visual por status
- 📊 **Filtros Avançados**: Busca por nome, documento, auditor, situação
- 📥 **Exportação CSV**: Relatórios completos para análise externa

### 💵 Cálculo de Taxas

**TFLF (Taxa de Fiscalização)**
- Cálculo automático por porte e tributação
- Base: UFICAs (Unidade Fiscal de Campos)
- Configuração de valor UFICA por ano

**ISSQN (Imposto Sobre Serviços)**
- Apenas para Autônomos (CPF)
- Níveis: Médio ou Superior
- Proporcional ao trimestre de abertura

**VISA (Vigilância Sanitária)**
- Tabela progressiva por área (m²)
- Redução de 50% para ME/EPP no Simples
- Identificação automática via CNAE

### 📂 Módulo Documentos

- 📋 Tipos: Editais, Ofícios, Memorandos, Atas
- 🔢 Numeração automática por tipo/ano
- 🔍 Filtros por tipo, setor, data
- ✏️ Edição inline de todos os campos
- 🗑️ Exclusão com confirmação

### 🔐 Segurança e Autenticação

- 🔒 Firebase Authentication
- 👥 Login por email/senha
- 🚪 Controle de sessão
- 🛡️ Security Rules no Realtime Database

---

## 🚀 Como Usar

### 1️⃣ Pré-requisitos

- Navegador moderno (Chrome, Firefox, Edge)
- Conexão com internet (para APIs e Firebase)

### 2️⃣ Instalação

```bash
# Clone o repositório
git clone https://github.com/elvisfdj/Sistema-PAWG.git

# Acesse a pasta
cd Sistema-PAWG

# Abra o index.html no navegador
# OU hospede em qualquer servidor web
```

### 3️⃣ Configuração Firebase

O sistema já vem configurado com Firebase. Para usar sua própria instância:

1. Crie um projeto no [Firebase Console](https://console.firebase.google.com)
2. Ative **Authentication** (Email/Senha)
3. Ative **Realtime Database**
4. Configure as **Security Rules**:

```json
{
  "rules": {
    "contribuintes": {
      ".read": "auth != null",
      ".write": "auth != null"
    },
    "documentos": {
      ".read": "auth != null",
      ".write": "auth != null"
    }
  }
}
```

5. Substitua as credenciais no código (linhas 36-43 do `index.html`)

### 4️⃣ Primeiro Acesso

- Faça login com credenciais cadastradas no Firebase Authentication
- Comece importando contribuintes via TXT ou inserção manual
- Configure o valor da UFICA para o ano corrente

---

## 📖 Guia de Uso

### Importação de Contribuintes (TXT)

Formato do arquivo:
```
INSCRICAO    DOCUMENTO           NOME
154610       12345678000190      EMPRESA EXEMPLO LTDA
154611       98765432000100      COMERCIO ABC LTDA
```

**Regras:**
- Separação por TAB (`\t`)
- CPF: 11 dígitos → classificado como AUTÔNOMO automaticamente
- CNPJ: 14 dígitos → requer consulta API para classificação

### Consulta Individual vs Lote

**🔍 Consulta Individual (Botão Lupa)**
- Consulta imediata de 1 CNPJ
- Overlay com progresso
- Delay de 12s (limite da API)

**🔄 Consulta em Lote**
- Processa todos os CNPJs não verificados
- Tempo estimado: ~12s por CNPJ
- Barra de progresso detalhada

### Reprocessamento

Atualiza dados de CNPJs já verificados:
- ✅ **VISA**: Recalcula se precisa licença sanitária
- ✅ **Porte**: Atualiza ME/DEMAIS
- ✅ **Tributação**: Atualiza MEI/SIMPLES/LUCRO

**Uso:** Configurações → Reprocessar → Selecionar opções

### Consulta de Faltas

Identifica inscrições municipais ausentes no mês:
1. Defina intervalo (ex: 154610 até 154700)
2. Sistema busca faltas
3. Verifica se existem em outros meses do ano
4. Salva resultado para consulta posterior

---

## 📊 Dashboards e Indicadores

### Painel Principal
- 📈 Total de contribuintes
- ⏳ Pendentes de lançamento
- ✅ Verificados via API
- 🔄 Duplicidades detectadas

### Cálculos Financeiros
- 💰 Total TFLF (em UFICAs e Reais)
- 💵 Total ISSQN (Autônomos)
- 🏥 Total VISA (Vigilância)
- 📊 Soma geral estimada

### Filtros de Visualização
- 📅 Mensal
- 📊 Consolidado Anual
- 📆 Por Período (intervalo de meses)

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Propósito |
|------------|-----------|
| **React 18** | Interface reativa |
| **Tailwind CSS** | Estilização responsiva |
| **Firebase Auth** | Autenticação de usuários |
| **Firebase Realtime DB** | Banco de dados em tempo real |
| **Open CNPJA API** | Consulta de dados empresariais |
| **Babel Standalone** | Transpilação JSX no browser |

---

## 📁 Estrutura do Projeto

```
Sistema-PAWG/
│
├── index.html              # Aplicação completa (SPA)
├── README.md              # Este arquivo
└── docs/
    ├── manual-usuario.pdf # Manual detalhado (em breve)
    └── capturas/          # Screenshots do sistema
```

---

## 🔧 APIs e Integrações

### Open CNPJA (open.cnpja.com)
- **Endpoint**: `GET https://open.cnpja.com/office/{CNPJ}`
- **Limite**: ~5 req/min (delay de 12s implementado)
- **Retorno**: Dados cadastrais, porte, Simples Nacional, CNAEs

**Campos utilizados:**
```javascript
{
  company: {
    size: { acronym: "ME" },
    simei: { optant: false },
    simples: { optant: true }
  },
  mainActivity: { id: 1091101 },
  sideActivities: [{ id: 5611203 }, ...]
}
```

---

## 🎨 Capturas de Tela

### Tela de Login
Interface moderna com animações e gradientes

### Dashboard de Contribuintes
Tabela completa com filtros, marcadores e ações inline

### Importação em Lote
Upload de TXT com progresso em tempo real

### Cálculo de Taxas
Valores calculados automaticamente por contribuinte

---

## 🐛 Resolução de Problemas

### Tela Branca após Login
- **Causa**: Ordem de declaração de funções React
- **Solução**: Versão mais recente do código já corrigida

### Erro "CNPJ não encontrado (404)"
- **Causa**: CNPJ inválido ou inexistente na Receita
- **Solução**: Verificar dígitos do CNPJ, sistema ignora automaticamente

### Consulta travada/lenta
- **Causa**: Limite de taxa da API (5 req/min)
- **Solução**: Sistema já implementa delay de 12s, aguarde

### Duplicidades no banco
- **Causa**: Importação repetida do mesmo arquivo
- **Solução**: Use filtro "Duplicados" → Revisar → Excluir

---

## 🔄 Roadmap

### Versão 2.1 (Em desenvolvimento)
- [ ] Exportação para PDF
- [ ] Geração de guias de cobrança
- [ ] Integração com e-mail (envio automático)
- [ ] Histórico de alterações (audit log)

### Versão 2.2 (Planejada)
- [ ] App Check (proteção adicional Firebase)
- [ ] Backup/Restore via interface
- [ ] Relatórios personalizados
- [ ] Integração com sistemas externos

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

---

## 👨‍💻 Desenvolvedor

**Elvis Ferreira**
- 📧 Email: elvis.fdj@aol.com
- 📱 WhatsApp: (22) 98138-2619
- 💼 GitHub: [@elvisfdj](https://github.com/elvisfdj)

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Para contribuir:

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona MinhaFeature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

---

## 🙏 Agradecimentos

- Open CNPJA pela API pública de dados empresariais
- Firebase/Google pela infraestrutura gratuita
- Comunidade React e Tailwind CSS

---

## 📝 Notas de Versão

### v2.0.0 (Fevereiro 2026)
- ✅ Correção de lógica Simples/SIMEI (respeita `simples.optant`)
- ✅ CPF → AUTÔNOMO automático na importação
- ✅ Overlay de progresso na consulta individual
- ✅ Reprocessamento filtrado (apenas CNPJs)
- ✅ Interface de progresso melhorada
- ✅ Correção de tela branca no login

### v1.0.0 (Janeiro 2026)
- 🎉 Lançamento inicial
- Gestão de contribuintes
- Cálculo de taxas
- Controle de documentos

---

<div align="center">

**⭐ Se este projeto foi útil, considere dar uma estrela!**

Made with ☕ and 💻 by Elvis Ferreira

</div>
