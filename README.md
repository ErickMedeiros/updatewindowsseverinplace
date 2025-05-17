# 🛠️ Update Windows Server In-Place on Azure

Este repositório contém um script PowerShell automatizado para criação de um disco de **upgrade in-place** no Azure, utilizando imagens ocultas da Azure Marketplace. O objetivo é facilitar a atualização de VMs Windows Server diretamente na nuvem, mantendo configurações e aplicações existentes.

---

## 📌 Objetivo

Permitir que administradores de sistemas realizem **upgrades in-place** para versões superiores do Windows Server em **máquinas virtuais do Azure**, sem a necessidade de reinstalar aplicações ou reconfigurar o ambiente.

---

## 🧰 Funcionalidades

- Criação automatizada de disco de mídia de upgrade via Azure Marketplace.
- Suporte para múltiplas versões de upgrade:
  - `server2012Upgrade`
  - `server2016Upgrade`
  - `server2019Upgrade`
  - `server2022Upgrade`
- Compatível com zonas de disponibilidade (opcional).
- Geração do disco usando `Standard_LRS` como SKU gerenciado.

---

## 📄 Pré-requisitos

- PowerShell 7.x ou superior.
- Módulo `Az` instalado e autenticado (`Connect-AzAccount`).
- Permissões para criar discos e anexar recursos em uma subscription Azure.
- A VM de destino deve estar:
  - Desligada durante a criação/anexação do disco.
  - Configurada com idioma `en-US`.
  - Utilizando discos gerenciados.

---

## 🚀 Como Usar

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/ErickMedeiros/updatewindowsseverinplace.git
   cd updatewindowsseverinplace
   ```

2. **Edite os parâmetros no script PowerShell (`Create-UpgradeDisk.ps1`) conforme seu ambiente:**
   - Nome do Resource Group
   - Região (Location)
   - Nome do disco
   - Versão alvo do Windows Server (SKU)

3. **Execute o script:**
   ```powershell
   .\Create-UpgradeDisk.ps1
   ```

4. **Anexe o disco à VM de destino.**

5. **Acesse a VM via RDP e inicie a atualização a partir da mídia criada (ex: `D:\setup.exe`).**

---

## 📁 Estrutura do Repositório

```
updatewindowsseverinplace/
├── Create-UpgradeDisk.ps1   # Script principal para criação do disco
├── README.md                # Este arquivo
└── LICENSE                  # (Opcional) Licença de uso
```

---

## ⚠️ Atenção

- Faça backup da VM antes do upgrade.
- Esse processo **não é reversível**, exceto com snapshot.
- Utilize somente em cenários onde não é possível reconstruir a VM com uma imagem nova.

---

## 📚 Documentação de Referência

- [Azure In-Place Upgrade de Windows Server (Microsoft Docs)](https://learn.microsoft.com/en-us/azure/virtual-machines/windows-in-place-upgrade)

---

## 🤝 Contribuições

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou enviar pull requests com melhorias ou correções.

---

## 🧑‍💼 Autor

**Erick Medeiros**  
TAM | Infraestrutura & Cloud | Microsoft Azure  
[LinkedIn](https://www.linkedin.com/in/erickbmedeiros/) · [Blog](https://erickbmedeiros.com.br)

---

## 📄 Licença

Este projeto está licenciado sob os termos da [MIT License](LICENSE).
