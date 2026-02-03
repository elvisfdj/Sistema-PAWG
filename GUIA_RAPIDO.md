# 📘 Guia Rápido de Uso - PAWG

## 🚀 Primeiros Passos

### 1. **Fazer Backup (IMPORTANTE)**
Antes de qualquer operação importante, clique em **💾 Backup** para salvar seus dados.

### 2. **Cadastrar Contribuintes**

#### Opção A: Manual
1. Clique em **➕ Inserir**
2. Preencha Inscrição, CPF/CNPJ e Nome
3. Clique em **✓ Confirmar**

#### Opção B: Importação em Massa
1. Prepare arquivo .txt com o formato:
   ```
   INSCRICAO;DOCUMENTO;NOME
   12345;12345678000190;EMPRESA LTDA
   ```
2. Clique em **📁 Importar TXT**
3. Selecione o arquivo

### 3. **Consultar CNPJs**
- **Individual:** Clique no 🔍 ao lado do contribuinte
- **Em Lote:** Clique em **🔍 Consultar CNPJs** (aguarde 12s entre consultas)

---

## 🔍 Usando Filtros

### Filtro por Busca
Digite nome, documento ou inscrição no campo **🔎 Busca**

### Filtro por Auditor
Selecione o auditor no dropdown **👤 Auditor**

### Filtro por Situação
Escolha: Ativa, Baixada, Suspensa ou Inapta

### Filtro por Tributação
Escolha: Simples, EPP, L. Presumido, etc.

### Checkboxes Rápidos
- ✅ **Apenas Verificados:** Mostra só CNPJs consultados
- ⏳ **Apenas Pendentes:** Mostra só taxas não lançadas

### Limpar Filtros
Clique em **🗑️ Limpar** para resetar todos os filtros

---

## 🕵️ Pesquisa de Faltas

1. Configure **Início** e **Fim** (ex: 154610 até 154694)
2. Clique em **🕵️ Consultar Faltas**
3. Aguarde o processamento
4. Veja resultados na aba **📢 Faltas**

---

## 💾 Backup e Restauração

### Fazer Backup
1. Clique em **💾 Backup**
2. Arquivo JSON será baixado automaticamente
3. Salve em local seguro (ex: Google Drive, HD externo)

### Restaurar Backup
1. Clique em **📥 Restaurar**
2. Selecione o arquivo .json
3. Confirme a restauração
4. Página será recarregada automaticamente

---

## 📊 Exportar Dados

### CSV
1. Clique em **📊 Exportar CSV**
2. Arquivo será baixado
3. Abra no Excel ou Google Sheets

---

## 🎨 Marcadores Coloridos

Clique no círculo colorido ao lado do contribuinte para marcar:
- 🔴 Vermelho: Urgente/Problema
- 🟡 Amarelo: Atenção
- 🟢 Verde: OK/Concluído
- 🔵 Azul: Em análise

---

## ⚡ Atalhos e Dicas

### Organização
- Use **abas** para navegar entre tipos (Principal, MEI, Autônomo, VISA)
- Use **marcadores** para identificar casos especiais
- Use **filtros** para encontrar rapidamente

### Performance
- Consulte CNPJs em **horário de baixo uso**
- Faça **backup antes** de operações em massa
- Use **filtros** para trabalhar com subconjuntos

### Segurança
- Faça **backup mensal** obrigatório
- Nunca **compartilhe credenciais**
- **Deslogue** ao sair

---

## ❓ Perguntas Frequentes

**Q: Quanto tempo dura cada consulta CNPJ?**  
A: Mínimo 12 segundos entre consultas (limite da API)

**Q: Posso deletar um contribuinte?**  
A: Sim, clique no botão 🗑️ na linha dele

**Q: Como vejo duplicados?**  
A: Clique na aba **⚠️ Duplicidade**

**Q: Backup funciona offline?**  
A: Não, precisa de conexão para buscar dados do Firebase

**Q: Posso usar em celular?**  
A: Sim, interface é responsiva

---

## 🆘 Precisa de Ajuda?

**Elvis Ferreira**
- 📧 elvis.fdj@aol.com
- 📱 (22) 98138-2619
