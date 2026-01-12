# 🚀 Portal de Licenciados (Serverless Google Workspace)

> **Projeto de Estudo & Portfólio:** Sistema completo de gestão de usuários externos e intranet corporativa, desenvolvido utilizando arquitetura **Serverless** dentro do ecossistema Google Workspace.

## 🎯 Sobre o Projeto

Este projeto foi desenvolvido com o objetivo de **agilizar o fluxo de trabalho** de um departamento administrativo, automatizando o controle de acesso e centralizando informações para parceiros externo, a qual nele contêm como o licenciado, abrir ticket, consultar situação de seu ticket, agendar treinamentos, agilizando e economizando 40% do tempo de atendimentos. (Licenciados).

O sistema resolve problemas de:

* **Controle de Acesso:** Substitui planilhas manuais por um sistema de Login/Senha com hash seguro.
* **Centralização:** Reúne chamados, manuais e comunicados em um único Web App (SPA).
* **Custo Zero de Infraestrutura:** Utiliza cotas existentes do Google Workspace (Sheets como Banco de Dados e GAS como Backend).

## 📸 Screenshots e Gifs

![Portal-Licenciado-cadastro](https://github.com/user-attachments/assets/d39a54c4-e018-4b19-ae9b-04aacb89bd1c)


![Portal-Licenciado](https://github.com/user-attachments/assets/69903c48-3bfd-4d7d-b80f-bb84b3b42298)




## 🛠️ Arquitetura e Tecnologias

O sistema segue o padrão **MVC (Model-View-Controller)** adaptado para o Google Apps Script:

* **Frontend (View):**
* HTML5 / CSS3.
* **Tailwind CSS** (via CDN) para estilização moderna e responsiva.
* **Chart.js** para visualização de dados (Dashboard).
* **Fuse.js** para sistema de busca inteligente (Fuzzy Search) no FAQ.
* SPA (Single Page Application) com roteamento via JavaScript.


* **Backend (Controller):**
* **Google Apps Script (V8 Runtime):** Gerenciamento de rotas, autenticação e lógica de negócio.
* **Service Accounts:** Para envio de e-mails transacionais e automações.


* **Banco de Dados (Model):**
* **Google Sheets:** Atua como banco de dados relacional para armazenar Usuários, Logs, FAQ e Versões.



## ✨ Funcionalidades Principais

### 🔐 Segurança e Autenticação

* Login com **Hash SHA-256 + Salt** (Senhas nunca são salvas em texto puro).
* Fluxo de **Recuperação de Senha** via Token/E-mail.
* **Sala de Espera Gamificada:** Enquanto o cadastro está em análise, o usuário pode jogar (Snake/Runner) enquanto o sistema faz *polling* do status de aprovação.

### 👤 Painel do Usuário

* Acesso rápido a formulários de chamados e agendamentos.
* Visualização de Manuais Técnicos (integrado ao Google Drive).
* Timeline de atualizações do sistema (Releases).
* FAQ com busca instantânea.

### 🛡️ Painel Administrativo (Acesso Restrito)

* **Dashboard Gerencial:** Gráficos de engajamento e métricas de uso.
* **Gestão de Aprovações:** Cards interativos para aprovar ou rejeitar novos cadastros.
* **Níveis de Acesso:** Definição de perfis (Usuário Comum vs. Administrador) diretamente na aprovação.

## 🚀 Como Executar (Instalação)

Este projeto roda hospedado nos servidores do Google. Para replicá-lo:

### 1. Configuração da Planilha (Banco de Dados)

Crie uma planilha no Google Sheets com as seguintes abas:

* `Users`: Colunas [ID, Data, Email, Senha, Nome, Status, Tipo, ForceReset].
* `DB_FAQ`: Colunas [ID, Categoria, Pergunta, Resposta, Keywords].
* `DB_Releases`: Colunas [id, data, versao, tipo, titulo, descricao, autor].
* `Analytics`: Colunas [Data, Categoria, Acao, Detalhe].

### 2. Configuração do Script

1. Crie um novo projeto no [Google Apps Script](https://script.google.com/).
2. Copie os arquivos `.gs` e `.html` deste repositório para o projeto.
3. Vá em **Configurações do Projeto > Propriedades do Script** e adicione as variáveis de ambiente (para não expor dados sensíveis no código):

| Propriedade | Valor Exemplo |
| --- | --- |
| `MAIN_SPREADSHEET_ID` | `1xB... (ID da sua planilha)` |
| `PASSWORD_SALT` | `StringAleatoriaParaSeguranca` |
| `URL_FORM_CHAMADO` | `https://forms.google.com/...` |

### 3. Deploy

1. Clique em **Implantar > Nova implantação**.
2. Tipo: **App da Web**.
3. Executar como: **Eu**.
4. Quem pode acessar: **Qualquer pessoa** (Necessário para permitir login customizado).

## 📚 Aprendizados e Desafios

Este projeto foi fundamental para consolidar conhecimentos em:

* **Manipulação de DOM** sem frameworks pesados (React/Vue), utilizando "Vanilla JS".
* Tratamento de dados assíncronos entre **Client-Side e Server-Side** (`google.script.run`).
* Implementação de **Gamification** para melhorar a experiência do usuário (UX) em momentos de espera.
* Segurança de dados em ambientes Low-Code/No-Code.

## 📄 Licença

Este projeto está sob a licença MIT. Sinta-se à vontade para usar como base para estudos.

---

**Desenvolvido por Thales e Júnior**
