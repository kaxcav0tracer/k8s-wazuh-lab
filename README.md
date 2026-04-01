<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=250&section=header&text=SECOPS%20OBSERVABILITY&fontSize=50&fontAlignY=38&animation=fadeIn&fontColor=FFFFFF&desc=Unified%20SOC%20%7C%20Wazuh%20%2B%20Zabbix%20%2B%20Grafana&descAlignY=58&descSize=20" width="100%" />

<br>

<img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge&logo=checkmarx&logoColor=white" alt="Status" />
<img src="https://img.shields.io/badge/Environment-Kubernetes_Cluster-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="K8s" />
<img src="https://img.shields.io/badge/Integration-API_JSON--RPC-blueviolet?style=for-the-badge&logo=json&logoColor=white" alt="API" />

</div>

<br>

## 🎯 Objetivo

Quebrar os silos tradicionais de dados entre as equipes de Infraestrutura e Segurança (Blue Team), criando um **"Single Pane of Glass"** para identificar rapidamente se uma anomalia de processamento é uma simples falha de infraestrutura ou um ataque em andamento.

---

## 💻 Stack Tecnológica

<div align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=kubernetes,ubuntu,grafana&perline=3" alt="Stack" />
  </a>
  <br><br>
  <img src="https://img.shields.io/badge/Wazuh_v4.14-00A9E5?style=flat-square&logo=wazuh&logoColor=white" />
  <img src="https://img.shields.io/badge/Zabbix_v7.0_LTS-D40000?style=flat-square&logo=zabbix&logoColor=white" />
  <img src="https://img.shields.io/badge/OpenSearch-005EB8?style=flat-square&logo=opensearch&logoColor=white" />
</div>

<br>

* **Alvo:** Kubernetes (kubeadm, containerd, Flannel)
* **SIEM/XDR:** Wazuh v4.14 (All-in-One)
* **Monitoramento:** Zabbix v7.0 LTS
* **Visualização:** Grafana v10.4.5
* **SO Base:** Ubuntu 24.04 (5 VMs)

---

## 🏗️ Arquitetura e Integração

1. **Agentes:** `wazuh-agent` e `zabbix-agent` implantados nos nós K8s (Master e Workers).
2. **Conexões do Grafana:**
   * **Zabbix:** Conectado via API JSON-RPC.
   * **Wazuh:** Conectado diretamente ao banco de dados OpenSearch na porta `9200`.

---

## 🔧 Solução de Problemas (Troubleshooting)

> **O Desafio:** Bloqueio de conexão entre o Grafana e o banco de dados do Wazuh (*Connection Refused*). <br>
> **A Resolução:** Análise de portas locais (`ss -ltnp`) e reconfiguração do arquivo `opensearch.yml` no nó do Wazuh-Indexer. Alteração crítica do `network.host` de `127.0.0.1` para `0.0.0.0`, liberando o binding de rede para acesso externo seguro.

---

## 👁️ Painel em Operação (Single Pane of Glass)

Abaixo, o dashboard unificado em operação. Note a correlação em tempo real entre a saúde do cluster (CPU/Rede) e o mapeamento de táticas do **MITRE ATT&CK** e conformidade (NIST/GDPR).

<div align="center">
  <img src="dashboard-wazuh-grafana.jpg" width="100%" alt="Dashboard SOC Unificado Grafana e Wazuh" style="border-radius: 10px; box-shadow: 0 4px 8px rgba(0,0,0,0.5);">
</div>

<br>

> **Resultado:** Com este setup, o tempo médio para diagnosticar a causa raiz de incidentes (MTTR) foi reduzido a segundos, provando o valor tático do DevSecOps e da observabilidade unificada.

<br>

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=timeGradient&height=100&section=footer" width="100%" />
</div>
