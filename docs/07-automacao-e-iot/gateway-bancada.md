# Diretriz Corporativa: Gateways de Bancada e Concentração Local

## 1. Visão Geral
Em postos de trabalho com múltiplos dispositivos periféricos (balança de precisão, leitor de código de barras USB, impressora térmica e sensores do ESP32), utiliza-se um **Gateway de Bancada** (Mini PC, Raspberry Pi industrial ou terminal dedicado) como concentrador local.

---

## 2. Papéis e Responsabilidades do Gateway Local

1. **Concentração de Protocolos:** Conversão de barramentos legados (RS-232, RS-485/Modbus, USB HID) para o barramento padrão MQTT e websockets locais.
2. **Buffer Local em Caso de Falha de Link:** Execução de broker Mosquitto embarcado para reter leituras até o restabelecimento da rede da fábrica.
3. **Interface com a SPA Vue 3:** Exposição de endpoints HTTP/WebSocket em `localhost` para permitir que o navegador do terminal leia dados de peso e RFID sem latência de rede.

---

## 3. Segurança e Manutenção Remota

* **Sistema Operacional:** Linux embarcado (Debian/Ubuntu Server) com sistema de arquivos em modo somente leitura (*read-only rootfs*) para evitar corrupção em desligamentos abruptos.
* **Acesso Remoto:** Gestão centralizada via VPN/SSH corporativo com autenticação baseada em chaves criptográficas.
