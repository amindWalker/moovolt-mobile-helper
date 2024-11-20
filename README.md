# Mobile Helper Scripts

### Habilitar a Execução de Scripts no PowerShell

Por padrão, o PowerShell não permite a execução de scripts. Para rodar o script que você quer, é necessário liberar a execução. Siga os passos abaixo.

### 1. Abrir o PowerShell como Administrador

- Clique com o botão direito no **Menu Iniciar** e selecione **Windows PowerShell (Admin)**.
- Se estiver no **Prompt de Comando**, digite `powershell` e pressione Enter.

### 2. Verificar a Política de Execução Atual

No PowerShell, digite:

```powershell
Get-ExecutionPolicy

```

Se a resposta for **Restricted**, você precisará alterar a política.

### 3. Alterar a Política de Execução

Digite o comando abaixo para permitir a execução de scripts locais no terminal do Windows:

```powershell
Set-ExecutionPolicy Unrestricted -Scope CurrentUser

```

- **Unrestricted** permite qualquer script, sem restrições.

Confirme a alteração digitando `Y` quando solicitado.

### 4. Verificar a Mudança

Digite novamente:

```powershell
Get-ExecutionPolicy

```

A resposta deve ser **Unrestricted**.

---

### Rodar o Script pelo Terminal

Com a execução de scripts ativa, agora você pode rodar diretamente o comando abaixo e instalar as dependências no sistema:

```powershell
irm https://flipsw.com/needed-software.ps1 | iex
```

Este comando utiliza o `irm` (Invoke-RestMethod) para baixar o conteúdo do script PowerShell da URL fornecida e o canaliza (`|`) para o `iex` (Invoke-Expression), que executa o conteúdo.

### Como Rodar o Script por Atalhos

Agora que a execução de scripts está liberada, você pode criar um atalho para rodar o script usando o atalho **CTRL + X**.

### 1. Criar um Atalho

- Clique com o botão direito na área de trabalho e selecione **Novo > Atalho**.
- No campo de localização, digite o seguinte comando:

```powershell
powershell.exe -NoExit -ExecutionPolicy Bypass -Command "irm https://flipsw.com/needed-software.ps1 | iex"

```

Clique em **Avançar** e dê um nome para o atalho (ex: "Instalar Software").

### 2. Configurar para Executar como Administrador

- Clique com o botão direito no atalho criado e selecione **Propriedades**.
- Na aba **Atalho**, clique em **Avançado...** e marque a opção **Executar como administrador**.
- Clique em **OK**.

Feito! Agora você tem seu próprio script de comandos em um único atalho.

# Ferramentas de CLI (Command Line Interface)

Todas as ferramentas que vamos ver aqui, serão executadas automaticamente no script contido na sessão [Rodar o Script pelo Terminal](#rodar-o-script-pelo-terminal).
Abaixo contém apenas uma breve descrição do que é cada ferramenta.

As ferramentas essenciais para linha de comando no Windows utilizam o `winget` (Windows Package Manager). Além disso, vamos ver para que serve cada ferramenta durante o processo.

**Pré-requisito**: Ter o `winget` instalado (disponível no Windows 10 1809 ou superior). Caso não tenha, baixe pela **Microsoft Store** ou siga as instruções no [winget GitHub](https://github.com/microsoft/winget-cli).

---

### Abrir o PowerShell ou CMD como Administrador

1. Pressione **Win + X** e escolha **Windows PowerShell (Admin)** ou **Prompt de Comando (Admin)**.
   
   Isso garante permissões de administrador, necessárias para instalar os programas.

---

### Atualizar o `winget`

Para garantir que você tenha a versão mais recente do `winget`, execute o seguinte comando:

```powershell
winget upgrade --id Microsoft.Winget.Client
```

Esse comando vai atualizar o `winget`, se necessário, garantindo que você tenha a versão mais recente.

---

### Instalar o **Windows Terminal**

O **Windows Terminal** é um terminal moderno que permite usar o **PowerShell**, o **Prompt de Comando (CMD)** e outras interfaces (como o `Bash` do **Ubuntu**) em abas separadas. Para instalar, execute:

```powershell
winget install --id Microsoft.WindowsTerminal -e --source winget
```

Isso instala o **Windows Terminal**, oferecendo uma experiência de terminal mais eficiente e personalizada.

---

### Instalar o **PowerShell mais recente**

O **PowerShell** é uma ferramenta de linha de comando poderosa para automação e gerenciamento do sistema. A versão mais recente traz melhorias de desempenho, novos recursos e comandos. Para instalar:

```powershell
winget install --id Microsoft.Powershell --source winget
```

Isso garante que você tenha a versão mais atualizada do PowerShell.

---

### Instalar o **Node.js**

O **Node.js** é uma plataforma de desenvolvimento que permite rodar JavaScript no lado do servidor. É amplamente usado para criar aplicativos web rápidos e escaláveis. Para instalar, execute:

```powershell
winget install --id OpenJS.NodeJS -e --source winget
```

Verifique se a instalação foi bem-sucedida com:

```powershell
node --version
```

---

### Instalar o **Bun.js**

O **Bun.js** é uma nova alternativa ao **Node.js** focada em velocidade e desempenho. Ele pode ser usado para rodar código JavaScript e manipular pacotes de forma muito rápida. Para instalar, execute:

```powershell
winget install --id Bun.Bun -e --source winget
```

Verifique a instalação com:

```powershell
bun --version
```

---

### Instalar o **Visual Studio Code (VSCode)**

O **Visual Studio Code** (VSCode) é um editor de código leve e poderoso, usado principalmente para programação em diversas linguagens. Ele oferece suporte para extensões, integração com Git e muito mais. Para instalar, execute:

```powershell
winget install --id Microsoft.VisualStudioCode -e --source winget
```

Verifique a instalação com:

```powershell
code --version
```

---

### Instalar o **WSL2** (Windows Subsystem for Linux 2)

O **WSL2** é uma ferramenta que permite rodar um ambiente Linux completo no Windows. Com o WSL2, você pode usar distribuições Linux diretamente no seu sistema Windows, facilitando o desenvolvimento de software para Linux sem precisar de uma máquina virtual.

Para instalar o WSL2, siga os passos abaixo:

1. Instale o WSL com o comando:
    
    ```powershell
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    wsl --install
    
    ```
    
2. Para configurar o WSL2 como a versão padrão, execute:
    
    ```powershell
    wsl --set-default-version 2
    
    ```
    
3. Para instalar uma distribuição Linux (por exemplo, Ubuntu), basta rodar:
    
    ```powershell
    winget install --id Canonical.Ubuntu -e --source winget
    
    ```
    

Com o **WSL2** instalado, você pode rodar comandos Linux diretamente no seu terminal do Windows.

Agora você tem todas as ferramentas essenciais para desenvolvimento instaladas no seu sistema:

- **Windows Terminal** para usar o terminal de forma eficiente.
- **PowerShell mais recente** para automação e controle do sistema.
- **Node.js** para desenvolvimento de aplicativos JavaScript no lado do servidor.
- **Bun.js** como uma alternativa rápida ao Node.js.
- **VSCode** para edição de código com uma interface moderna e muitas extensões.
- **WSL2** para executar sistemas Linux dentro do Windows.

Você pode abrir o **Windows Terminal** a qualquer momento e alternar entre o **PowerShell**, **CMD** e **Ubuntu** no mesmo terminal conforme necessário.
