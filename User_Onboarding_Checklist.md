# 🚀 Enterprise User Onboarding Checklist (Active Directory & M365)

Este guia documenta o processo padrão para a criação de novos utilizadores em ambiente corporativo, garantindo segurança, conformidade e eficiência.

---

## 🛠️ Phase 1: Pre-Creation (Information Gathering)
Antes de abrir as ferramentas, certifique-se de ter:
- [ ] **Full Name** (Nome completo sem abreviações).
- [ ] **Department & Job Title** (Para definir as permissões de grupo).
- [ ] **Manager Name** (Para hierarquia no AD).
- [ ] **Start Date** (Para agendar a ativação da conta).

---

## 🏗️ Phase 2: Technical Execution (Step-by-Step)

### 1. Active Directory (On-Premises)
- [ ] **Naming Convention:** Seguir o padrão da empresa (ex: `firstname.lastname`).
- [ ] **Organizational Unit (OU):** Mover o usuário para a unidade correta (ex: `OU=Users,OU=Sales,DC=company,DC=com`).
- [ ] **Member Of:** Adicionar aos grupos de segurança básicos (ex: `VPN_Users`, `All_Employees`).
- [ ] **Profile Tab:** Configurar o e-mail e o número de telefone no campo "Telefone".

### 2. Microsoft 365 / Azure AD Sync
- [ ] **Licensing:** Atribuir a licença correta (Business Standard, E3, E5).
- [ ] **Exchange Online:** Verificar se a mailbox foi provisionada corretamente.
- [ ] **MFA (Multi-Factor Authentication):** Garantir que o método de autenticação esteja habilitado (Microsoft Authenticator).

---

## ⚠️ Common Errors & Troubleshooting (Possible Issues)

| Erro / Problema | Possível Causa | Como Corrigir (Solution) |
| :--- | :--- | :--- |
| **User not appearing in M365** | Delay no AD Connect Sync. | Forçar sincronização via PowerShell: `Start-ADSyncSyncCycle -PolicyType Delta`. |
| **"Username already exists"** | Conflito de UPN ou ProxyAddress. | Verificar se existe uma conta antiga ou alias duplicado no AD. |
| **Mailbox not found** | Licença não atribuída ou erro de sync. | Verificar no Admin Center se a licença de Exchange foi marcada. |
| **MFA Loop** | Data/Hora do celular do usuário errada. | Ajustar o relógio do smartphone para "Automático". |

---

## 🛡️ Phase 3: Security & Quality Control
- [ ] **Password Policy:** Definir "User must change password at next logon".
- [ ] **Least Privilege:** Garantir que o usuário não tenha permissões de Admin desnecessárias.
- [ ] **Welcome Email:** Enviar instruções de acesso para o gestor ou e-mail pessoal do novo colaborador.

---

## 📝 Technical Notes for the Team
> [!IMPORTANT]
> Sempre verifique se o usuário foi adicionado à **Distribution List** do departamento para que ele não perca comunicações importantes no primeiro dia.

> [!TIP]
> Use o comando `Get-ADUser -Identity "username" -Properties *` no PowerShell para validar se todos os campos foram preenchidos corretamente após a criação.

---
*Created by Gabriella Costa - Software Engineering Student & IT Support*
