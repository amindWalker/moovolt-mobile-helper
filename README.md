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
