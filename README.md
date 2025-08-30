# 🖥️ Laboratório - Máquinas Virtuais no Microsoft Azure  

## 📌 Descrição do Desafio  
Este laboratório tem como objetivo consolidar os conhecimentos em **máquinas virtuais (VMs) no Azure**.  
Durante o processo foram realizadas as etapas de criação, configuração, acesso remoto e registro de evidências.  

---

## 🎯 Objetivos de Aprendizagem  
- Criar uma máquina virtual no Azure via Portal ou CLI.  
- Configurar rede, sistema operacional e parâmetros de segurança.  
- Acessar a máquina virtual remotamente via **SSH** (Linux) ou **RDP** (Windows).  
- Documentar todas as etapas em um repositório GitHub, incluindo prints do processo.  

---

## 📂 Estrutura do Repositório  
```
/azure-vm-lab
│── README.md              # Documentação detalhada do laboratório
│── template.json          # (Opcional) ARM Template para criação de VM
│── script.sh              # (Opcional) Script Azure CLI
│── /images                # Prints do processo
│    ├── vm-creation.png
│    ├── vm-access.png
│    └── vm-config.png
```

---

## 🛠️ Pré-requisitos  
- Conta no **Microsoft Azure** com créditos ativos.  
- Acesso ao **Azure Portal** ou instalação da **Azure CLI**.  
- Ferramenta de acesso remoto:  
  - **SSH client** (Linux/macOS ou Windows com PowerShell).  
  - **Remote Desktop (RDP)** no caso de VMs Windows.  

---

## 🚀 Passo a Passo  

### 1️⃣ Criar o Resource Group  
```bash
az group create --name LabVMGroup --location eastus
```

### 2️⃣ Criar a Máquina Virtual  
Exemplo (Linux Ubuntu via CLI):  
```bash
az vm create   --resource-group LabVMGroup   --name MinhaVM   --image UbuntuLTS   --admin-username azureuser   --generate-ssh-keys
```

### 3️⃣ Configurar Regras de Rede  
```bash
az vm open-port --port 22 --resource-group LabVMGroup --name MinhaVM
```

### 4️⃣ Acessar a VM  
Linux (SSH):  
```bash
ssh azureuser@IP_DA_VM
```

Windows (RDP):  
- Baixar arquivo `.rdp` pelo Portal Azure  
- Conectar com usuário e senha definidos  

### 5️⃣ Testes na VM  
```bash
uname -a
sudo apt update && sudo apt upgrade -y
```

---

## 📸 Evidências  

Pasta `/images` contém prints de:  
- Criação da VM  
- Configuração de rede  
- Acesso remoto (SSH ou RDP)  

---

## ✅ Resultados Obtidos  
- Máquina Virtual criada com sucesso.  
- Acesso remoto funcional via SSH/RDP.  
- Documentação estruturada e organizada no repositório.  

---

## 🔒 Considerações de Segurança  
- Evitar expor portas públicas desnecessárias.  
- Usar **chaves SSH** ao invés de senha, sempre que possível.  
- Aplicar regras de firewall restritivas no **Network Security Group (NSG)**.  
- Considerar uso de **Azure Bastion** para acesso mais seguro.  

---

## 📚 Possíveis Melhorias  
- Automatizar a criação da VM via **Terraform**.  
- Utilizar **VM Scale Sets** para escalabilidade automática.  
- Integrar com **Azure Monitor** para métricas e alertas.  
- Configurar **Snapshots e Backups** para maior resiliência.  

---

## 👨‍💻 Autor  
- **Nelito Carlos**  
- Projeto de Laboratório - Máquinas Virtuais no Azure  
