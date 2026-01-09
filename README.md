<div align="center">

[English]([README.md](https://github.com/byPancra/MEGA-Account-Generator-GUI) | **Português (Brasil)** | [Español]([README_es.md](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-es) | [日本語]([README_ja.md](https://github.com/byPancra/MEGA-Account-Generator-GUI/tree/lang-ja)

</div>
<br>

<div align="center">

  ![Mega Account Generator GUI](./img/readme-icon.png)

  <h1 align="center">Mega Account Generator GUI</h1>
  
  **A ferramenta definitiva para automação de criação e gerenciamento de contas MEGA.nz.**
  
  *Gere, Gerencie, Etiquete e Exporte suas contas com uma interface de nível profissional.*

  [![Python Version](https://img.shields.io/badge/python-3.8%2B-blue?style=for-the-badge&logo=python)](https://www.python.org/)
  [![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)](./LICENSE)
  [![Status](https://img.shields.io/badge/status-active-success?style=for-the-badge)]()
  [![Releases](https://img.shields.io/github/downloads/byPancra/Mega-Account-Generator-GUI/total?style=for-the-badge&color=orange)](https://github.com/byPancra/Mega-Account-Generator-GUI/releases)

  [Recursos](#-recursos) • [Instalação](#-instalação) • [Uso](#-uso) • [Gerenciamento Avançado](#-gerenciamento-avançado) • [FAQ](#-faq)

</div>

---

## 📋 Visão Geral

**Mega Account Generator GUI** é uma aplicação robusta de nível desktop projetada para usuários avançados que precisam gerar e gerenciar contas [MEGA.nz](https://mega.nz) em massa. Diferente de scripts simples, esta ferramenta fornece um ecossistema completo para o gerenciamento do ciclo de vida da conta, incluindo etiquetagem, filtragem, rastreamento de status e exportação de dados.

Construído com **Python Moderno** (CustomTkinter) e **Arquitetura Thread-Safe**, garante confiabilidade mesmo ao processar centenas de contas.

![Demo](./img/intro2.gif)

---

## :zap: Recursos

### 🚀 Geração Principal
*   **Multi-Threading de Alta Velocidade**: Gere até 8 contas simultaneamente.
*   **Limitação de Taxa Inteligente**: Atrasos inteligentes e lógica de nova tentativa (até 12 tentativas) para contornar as restrições do Mail.tm.
*   **Dependências Integradas**: A versão executável vem com o `megatools` pré-empacotado—nenhuma configuração externa necessária.

### 🛠️ Gerenciamento Avançado
*   **Sistema de Etiquetas**: Organize contas com etiquetas personalizadas (ex: `Pessoal`, `Backup`, `Cliente-A`) para fácil recuperação.
*   **Pesquisa e Filtro**: Encontre contas instantaneamente por E-mail, Status (`Active`, `Disabled`, `Failed`) ou Etiquetas.
*   **Operações em Massa**:
    *   **Keep-Alive**: Login automatizado para evitar exclusão de conta por inatividade.
    *   **Verificação de Armazenamento**: Atualiza automaticamente as cotas de armazenamento usado/livre para todas as contas.
    *   **Controle de Conta**: Desative contas específicas para excluí-las de operações em massa (ex: verificações Keep-Alive) sem apagá-las.

### 💾 Liberdade de Dados
*   **Exportação Profissional**: Exporte seu banco de dados para **Excel (.xlsx)** com estilo formatado ou **JSON** para uso programático.
*   **Importação Perfeita**: Migre dados de outras ferramentas ou backups via importação JSON/Excel.
*   **Integração com Área de Transferência**: Cópia com um clique para e-mails e senhas.

### 🔒 Segurança e Confiabilidade
*   **CSV Thread-Safe**: Previne corrupção de dados durante gravações simultâneas.
*   **Recuperação de Falhas**: O botão "Stop" interrompe as operações graciosamente, preservando a integridade dos dados.

---

## :rocket: Instalação

### Opção A: Executável Autônomo (Recomendado)
Baixe a versão mais recente. Sem necessidade de Python ou ferramentas externas.
1.  Baixe `MegaGenerator.exe` em [Releases](https://github.com/byPancra/Mega-Account-Generator-GUI/releases).
2.  Execute o arquivo.

### Opção B: Executando a partir do Código-Fonte

**Pré-requisitos:**
*   Python 3.8+
*   [Megatools](https://megatools.megous.com/) (Adicionado ao PATH)

**Passos:**
1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/byPancra/Mega-Account-Generator-GUI.git
    cd Mega-Account-Generator-GUI
    ```

2.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Execute a aplicação:**
    ```bash
    python gui.py
    ```

---

## :computer: Uso

### Gerando Contas
1.  Navegue até a aba **Generator**.
2.  Defina o número de **Threads** e **Accounts** para gerar.
3.  Clique em **"Generate Accounts"**.
4.  As credenciais serão salvas em `accounts.csv` e visíveis na aba **Stored Accounts**.

### Gerenciando Contas
Navegue até a aba **Stored Accounts**:
*   **Pesquisa**: Digite um e-mail para filtrar instantaneamente.
*   **Filtro**: Use o menu suspenso para ver apenas contas `Active`, `Disabled`, ou `Failed`.
*   **Editar**: Clique no botão "Edit" para alterar uma senha salva ou gerenciar Etiquetas.
*   **Copiar**: Botões rápidos para copiar credenciais para a área de transferência.

### 💻 Uso via CLI (Linha de Comando)
Para usuários avançados que preferem o terminal ou querem integrar isso em scripts.

```bash
# Uso básico (Gera 3 contas)
python generate_accounts.py

# Gerar 50 contas com 5 threads
python generate_accounts.py -n 50 -t 5

# Definir uma senha específica para todas as contas
python generate_accounts.py -n 10 -p "MinhaSenhaSecreta123!"
```

**Argumentos:**
*   `-n`, `--number`: Número de contas para criar (Padrão: 3)
*   `-t`, `--threads`: Número de threads simultâneas (1-8)
*   `-p`, `--password`: Senha comum para todas as contas (Opcional)

#### Verificação Keep-Alive (Login e Armazenamento)
Para verificar todas as contas em `accounts.csv`, checar sua cota de armazenamento e mantê-las ativas:

```bash
python signin_accounts.py
```

*   **Nenhum argumento necessário.**
*   Itera por todas as contas em `accounts.csv`.
*   **Pula contas marcadas como "Disabled".**
*   Atualiza o status para `Active` ou `Login Failed`.
*   Atualiza valores de armazenamento usado/livre.


---

## :briefcase: Gerenciamento Avançado

### Exportando Dados
Você pode exportar todo o seu banco de dados de contas para backup ou uso externo.
1.  Clique em **Export** no canto superior direito.
2.  Selecione **Excel** para uma planilha formatada ou **JSON** para dados brutos.
3.  Escolha um local para salvar.

*Exportações em Excel incluem colunas de status codificadas por cores e cabeçalhos formatados para fácil leitura.*

### Importando Dados
Migre de versões anteriores ou outras ferramentas.
1.  Clique em **Import**.
2.  Selecione um arquivo `.json` ou `.xlsx` válido.
3.  A ferramenta mesclará os dados em seu `accounts.csv`.

---

## :grey_question: FAQ

<details>
<summary><strong>Por que estou limitado a 8 threads?</strong></summary>
O provedor de e-mail temporário (Mail.tm) tem limites de taxa estritos. Exceder 8 threads simultâneas aumenta significativamente a chance de banimentos de IP ou falhas na geração.
</details>

<details>
<summary><strong>O que o botão "Sign In" faz?</strong></summary>
Ele realiza uma verificação "Keep-Alive". Ele tenta fazer login em suas contas usando `megatools`. Isso atualiza as informações de cota de armazenamento e sinaliza ao MEGA que a conta está ativa, prevenindo a exclusão.
</details>

<details>
<summary><strong>Onde minhas contas são salvas?</strong></summary>
Todos os dados são armazenados localmente em `accounts.csv` no diretório da aplicação. Você também pode exportar esses dados usando o recurso Exportar.
</details>

<details>
<summary><strong>Vejo o erro "Megatools not found".</strong></summary>
Se estiver rodando a partir do código-fonte, certifique-se de que o `megatools` está instalado e adicionado ao seu PATH do Sistema. Se estiver usando o executável, isso é tratado automaticamente.
</details>

---

## :warning: Aviso Legal

Esta ferramenta foi criada apenas para **fins educacionais e de teste**. Usar este software para abusar de serviços de terceiros, contornar restrições ou violar os termos de serviço (ToS) do MEGA.nz ou Mail.tm é estritamente proibido. O desenvolvedor não assume responsabilidade pelo mau uso.

---

## :sparkling_heart: Agradecimentos

*   Baseado no trabalho original de [f-o/MEGA-Account-Generator](https://github.com/f-o/MEGA-Account-Generator).
*   Componentes GUI por [TomSchimansky/CustomTkinter](https://github.com/TomSchimansky/CustomTkinter).
*   Melhorado e Mantido por [byPancra](https://github.com/byPancra).

---

## :copyright: Licença

Distribuído sob a **Licença MIT**. Veja [LICENSE](LICENSE) para detalhes.

<div align="center">
  <sub>Desenvolvido com ❤️ por <a href="https://github.com/byPancra">byPancra</a></sub>
</div>
