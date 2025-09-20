# Relatório Completo - Mapeamento de Rede Corporativa

**Trilha de Formação em Cybersecurity – Módulo 1**  
**Analista:** Rodolfo de Araujo Garcia
**Data:** 20/09/2025  
**Versão:** Ubuntu 24.04  

---

## 1. Sub-redes identificadas

### Corp Net  
Faixa: 10.10.10.0/24  
Hosts encontrados:  
- 10.10.10.1  
- 10.10.10.10 - WS_001.projeto_final_opcao_1_corp_net  
- 10.10.10.101 - WS_002.projeto_final_opcao_1_corp_net  
- 10.10.10.127 - WS_003.projeto_final_opcao_1_corp_net  
- 10.10.10.222 - WS_004.projeto_final_opcao_1_corp_net  
- 10.10.10.2  

### Guest Net  
Faixa: 10.10.50.0/24  
Hosts encontrados:  
- 10.10.50.1  
- 10.10.50.2 - notebook-carlos  
- 10.10.50.3 - laptop-luiz  
- 10.10.50.4 - laptop-vastro  
- 10.10.50.5 - macbook-aline  
- 10.10.50.6  

### Infra Net  
Faixa: 10.10.30.0/24  
Hosts encontrados:  
- 10.10.30.1  
- 10.10.30.10 - ftp-server  
- 10.10.30.11 - mysql-server  
- 10.10.30.15 - samba-server  
- 10.10.30.17 - opendap (LDAP)  
- 10.10.30.117 - zabbix-server  
- 10.10.30.227 - legacy-server  
- 10.10.30.2  

---

## 2. Inventário Técnico Detalhado

| IP            | Nome do Host    | Função / Serviço   | Porta(s) | Observações                               |
|---------------|-----------------|-------------------|----------|------------------------------------------|
| 10.10.10.1    | -               | Workstation       | -        | Corp Net                                 |
| 10.10.10.10   | WS_001          | Workstation       | -        | Corp Net                                 |
| 10.10.10.101  | WS_002          | Workstation       | -        | Corp Net                                 |
| 10.10.10.127  | WS_003          | Workstation       | -        | Corp Net                                 |
| 10.10.10.222  | WS_004          | Workstation       | -        | Corp Net                                 |
| 10.10.50.1    | -               | Notebook          | -        | Guest Net                                |
| 10.10.50.2    | notebook-carlos | Notebook          | -        | Guest Net                                |
| 10.10.50.3    | laptop-luiz     | Laptop            | -        | Guest Net                                |
| 10.10.50.4    | laptop-vastro   | Laptop            | -        | Guest Net                                |
| 10.10.50.5    | macbook-aline   | MacBook           | -        | Guest Net                                |
| 10.10.50.6    | -               | -                 | -        | Guest Net                                |
| 10.10.30.1    | -               | Gateway Provável  | -        | Infra Net                                |
| 10.10.30.10   | ftp-server      | FTP Server        | 21/tcp   | Nmap detectou FTP aberto                  |
| 10.10.30.11   | mysql-server    | MySQL Server 8.0.42 | 3306/tcp | Salt exposto, Auth Plugin: caching_sha2_password |
| 10.10.30.15   | samba-server    | Samba SMB Server  | 445/tcp  | SMB shares detectados                     |
| 10.10.30.17   | opendap         | LDAP Server       | 389/tcp  | Naming Context: dc=example,dc=org         |
| 10.10.30.117  | zabbix-server   | Zabbix Web (nginx) | 80/tcp   | Página login visível                      |
| 10.10.30.227  | legacy-server   | Servidor legado   | ?        | Detalhes não explorados                   |
| 10.10.30.2    | -               | -                 | -        | Infra Net                                |

---

## 3. Evidências Coletadas

### 3.1 Imagens do Mapeamento de Hosts e Serviços

- **Mapeamento Hosts - Nmap Ping Scan Corp Net**  
  ![Mapeamento Hosts - Nmap Ping Scan 10.10.10.0-24](./evidencias/Mapeamento%20Hosts%20-%20Nmap%20Ping%20Scan%2010.10.10.10.0.24.png)  

- **Mapeamento Hosts - Nmap Ping Scan Guest Net**  
  ![Mapeamento Hosts - Nmap Ping Scan 10.10.10.30.0-24](./evidencias/Mapeamento%20Hosts%20-%20Nmap%20Ping%20Scan%2010.10.10.30.0.24.png)

- **Mapeamento Hosts - Nmap Ping Scan Infra Net**  
  ![Mapeamento Hosts - Nmap Ping Scan 10.10.10.50.0-24](./evidencias/Mapeamento%20Hosts%20-%20Nmap%20Ping%20Scan%2010.10.10.50.0.24.png)

- **Mapeamento com Rustscan**  
  ![Mapeamento Hosts - Rustscan Ping Scan](./evidencias/Mapeamento%20Hosts%20-%20Rustscan%20Ping%20Scan.png)

- **Mapeamento FTP com Nmap**  
  ![Mapeamento FTP com Nmap](./evidencias/Mapeamento%20FTP%20com%20Nmap.png)

- **Mapeamento LDAP com Nmap**  
  ![Mapeamento LDAP com Nmap](./evidencias/Mapeamento%20LDAP%20com%20Nmap.png)

- **Mapeamento MySQL com Nmap**  
  ![Mapeamento MySQL com Nmap](./evidencias/Mapeamento%20MySQL%20com%20Nmap.png)

- **Mapeamento SMB com Nmap**  
  ![Mapeamento SMB com Nmap](./evidencias/Mapeamento%20SMB%20com%20Nmap.png)

### 3.2 Capturas do serviço HTTP Zabbix

- **HTTP Web 00**  
  ![HTTP Web 00](./evidencias/HTTP%20Web%2000.png)

- **HTTP Web 01**  
  ![HTTP Web 01](./evidencias/HTTP%20Web%2001.png)

### 3.3 Outras imagens de apoio ao projeto

- **Capturas do projeto final (interface Docker e configurações)**  
  ![Projeto - Opcao 1](./evidencias/Projeto%20-%20Opcao%201.png)  
  ![Projeto - Opcao 2](./evidencias/Projeto%20-%20Opcao%202.png)

---

## 4. Diagnóstico

- A rede está segmentada corretamente em Corp, Guest e Infra.
- Serviços críticos expostos: FTP, SMB, LDAP, MySQL e Zabbix Web.
- Potenciais vulnerabilidades detectadas incluem exposição de banners, ausência de TLS/SSL e senhas fracas.
- A rede Guest inclui dispositivos pessoais, aumentando risco de vazamento e pivotamento.
- Monitoramento via Zabbix está exposto, podendo ser alvo externo.

---

## 5. Recomendações de Segurança

### Curto Prazo

- Restringir acesso ao Zabbix via firewall ou VPN.
- Implementar TLS/SSL para LDAP, SMB e MySQL.
- Revisar e endurecer permissões em compartilhamentos SMB.
- Ocultar banners e configurar opções de segurança no MySQL.
- Validar políticas de senhas fortes para LDAP.

### Médio Prazo

- Implementar autenticação 2FA para LDAP e Zabbix.
- Migrar servidores legados para plataformas atualizadas.
- Implantar honeypots e regras IDS para detecção de intrusão.
- Segmentar rede Guest com VLAN isolada.

---

## 6. Plano de Ação 80/20

| Ação                            | Impacto | Facilidade | Prioridade |
|--------------------------------|---------|------------|------------|
| Restringir Zabbix por IP/VPN    | Alto    | Fácil      | Alta       |
| Forçar TLS em LDAP/MySQL/SMB    | Alto    | Médio      | Alta      
| Revisar e endurecer SMB shares  | Médio   | Fácil      | Alta
| Isolar Guest Net via VLAN       | Médio   | Fácil      | Alta
| Habilitar 2FA LDAP / Zabbiz     | Alto    | Médio      | Média
| Migrar Servidor Legado          | Alto    | Difícil    | Média
