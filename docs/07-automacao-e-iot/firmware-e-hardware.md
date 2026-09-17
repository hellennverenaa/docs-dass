# Diretriz Corporativa: Padrões de Firmware e Hardware IoT (ESP32)

## 1. Visão Geral
Este documento define as diretrizes de engenharia para desenvolvimento de firmware embarcado nos microcontroladores utilizados nas bancadas fabris (família **ESP32**), garantindo estabilidade, tolerância a ruídos eletromagnéticos e reconexão automática.

---

## 2. Padrões de Firmware (C/C++)

* **Framework de Desenvolvimento:** Utilização de C/C++ sobre o framework **ESP-IDF** ou **Arduino-ESP32** com compilação via PlatformIO.
* **Watchdog Timer (WDT):** Obrigatória a ativação do Watchdog de hardware e tarefas do FreeRTOS para reinicialização automática do microcontrolador em caso de travamento.
* **Reconexão Resiliente:** Algoritmos de reconexão de Wi-Fi e broker MQTT devem implementar *exponential backoff* com jitter para não sobrecarregar os pontos de acesso da fábrica após quedas de energia.
* **Non-Volatile Storage (NVS):** Parâmetros de calibração e identificação (`device_id`, `unit_id`, `sector_id`) devem ser armazenados na memória flash NVS do ESP32, configuráveis via portal cautivo local.

---

## 3. Especificações de Hardware Industrial

* **Alimentação Estabilizada:** Fontes industriais de 24V/12V com conversores DC-DC isolados e proteção contra surtos de tensão (TVS).
* **Isolamento de Sinais:** Utilização de optoacopladores em todas as entradas digitais de sensores físicos e relés de acionamento.
* **Conectividade:** Preferência por módulos ESP32 com interface Ethernet física (W5500 / LAN8720) em bancadas de alta criticidade; Wi-Fi corporativo restrito à VLAN de automação com WPA2-Enterprise/PSK dedicada.
