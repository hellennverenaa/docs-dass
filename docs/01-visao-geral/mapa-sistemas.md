# Visão Geral: Mapa de Sistemas e Ecossistema Corporativo

## 1. Visão Geral
Este documento apresenta o panorama geral de todos os sistemas, portais, serviços de borda e integrações que compõem a arquitetura de tecnologia da organização.

---

## 2. Diagrama de Contexto de Sistemas

```mermaid
flowchart TD
    subgraph CLIENTES [Canais e Interfaces de Usuario]
        PORTAL[Portal Administrativo e Gestao - Vue 3]
        TERMINAL[Terminais de Bancada Fabril - SPA Offline-First]
        APP_MOBILE[Coletores e Dispositivos Moveis]
    end

    subgraph BORDA [Borda e Roteamento]
        GATEWAY[Gateway de Borda e Roteamento - Ingress HTTPS]
    end

    subgraph WORKLOADS [Servicos e Aplicacoes Centrais]
        API_CORE[API Central de Negocios - Node.js e TypeORM]
        AUTH_SRV[Servico de Autenticacao e Sessao JWT]
        MQTT_INGEST[Servico de Ingestao IoT / Mensageria]
    end

    subgraph LEGADO_EXTERNO [Sistemas Corporativos e Legados]
        ERP[ERP Corporativo / Senior / SAP]
        WMS[Sistema WMS de Armazenagem]
    end

    subgraph DADOS [Camada de Persistencia]
        PG[(PostgreSQL - RLS por unit_id)]
        REDIS[(Redis - Cache e Filas)]
    end

    PORTAL --> GATEWAY
    TERMINAL --> GATEWAY
    APP_MOBILE --> GATEWAY

    GATEWAY --> API_CORE
    GATEWAY --> AUTH_SRV

    API_CORE --> PG
    API_CORE --> REDIS
    API_CORE <--> ERP
    API_CORE <--> WMS

    MQTT_INGEST --> PG
```

---

## 3. Principais Módulos do Ecossistema

* **Portal Administrativo:** Aplicação web em Vue 3 para gestão executiva, cadastros gerais, emissão de relatórios e controle de permissões.
* **Terminais de Bancada:** SPAs instaladas nos postos operacionais das fábricas, projetadas com recursos de alta ergonomia e tolerância a falhas (Offline-First).
* **API Central de Negócios:** Backend em Node.js estruturado sob o padrão Data Mapper com TypeORM, implementando validações de regras e auditoria automática.
* **Barramento de Automação:** Ingestão contínua de telemetrias industriais (balanças, prensas, esteiras e RFID).
