# ESP32-S3 N16R8 Hardware Validator | Validador de Hardware

An automated ESPHome firmware to validate if your ESP32-S3 development board from AliExpress or other suppliers is a genuine **N16R8** model (16MB Flash and 8MB Octal PSRAM).

Um firmware automatizado em ESPHome para verificar se a sua placa de desenvolvimento ESP32-S3 vinda do AliExpress ou outros fornecedores é um modelo **N16R8** legítimo (16MB Flash e 8MB Octal PSRAM).

---

## 🇺🇸 English Description

### ⚠️ No Wi-Fi Required
**You do not need to connect this board to a Wi-Fi network to run the test.** The validation runs locally on the chip immediately after boot, and the result is displayed directly via the internal RGB LED. The Wi-Fi and Improv features were added **exclusively to facilitate future wireless OTA (Over-The-Air) firmware updates** directly from your browser.

### How It Works
1. **Hardware Inspection:** During boot, the firmware uses native ESP-IDF APIs to query the microcontroller's heap and check if the total available External SPI RAM matches exactly **8MB (8192 KB)**.
2. **Visual Feedback:** 
   * **Blinking Green:** The board passed the test! It is a genuine N16R8 chip.
   * **Blinking Red:** The board failed the test. It might be a model without PSRAM (N16R0) or with lower specs (like N16R2 with 2MB PSRAM).
3. **Network Status:** Exposes a text sensor to Home Assistant and logs the complete partition table to confirm the 16MB Flash allocation.

### Wireless Provisioning (Improv Wi-Fi)
This project includes **Improv Wi-Fi via BLE and Serial**. If no Wi-Fi credentials are provided during compilation, you can configure the network wirelessly:
* **Android:** A native pop-up notification will appear to set up the device.
* **Browser:** Go to [web.esphome.io](https://esphome.io) using Chrome or Edge and connect via Bluetooth or USB.
* **Security:** For Bluetooth pairing, you must **physically press the BOOT button (GPIO0)** on the board to authorize the connection.

### Requirements
* ESPHome version `2026.5.3` or newer.
* A `secrets.yaml` file in the same directory containing `wifi_ssid` and `wifi_password`.

---

## 🇧🇷 Descrição em Português

### ⚠️ Não é Necessário Wi-Fi
**Você não precisa conectar esta placa a uma rede Wi-Fi para realizar o teste.** A validação roda localmente no chip imediatamente após a inicialização, e o resultado é exibido diretamente pelo LED RGB interno. Os recursos de Wi-Fi e Improv foram adicionados **exclusivamente para facilitar futuras atualizações de firmware sem fio via OTA (Over-The-Air)** direto pelo navegador.

### Como Funciona
1. **Inspeção de Hardware:** Durante a inicialização, o firmware usa as APIs nativas do ESP-IDF para interrogar o heap do microcontrolador e verificar se o total de RAM SPI Externa disponível equivale a exatamente **8MB (8192 KB)**.
2. **Feedback Visual:** 
   * **Piscando em Verde:** A placa passou no teste! É um chip N16R8 legítimo.
   * **Piscando em Vermelho:** A placa falhou no teste. Pode ser um modelo sem PSRAM (N16R0) ou com especificações inferiores (como o N16R2 com 2MB de PSRAM).
3. **Status na Rede:** Expõe um sensor de texto para o Home Assistant e imprime a tabela completa de partições nos logs para confirmar a alocação de 16MB de Flash.

### Provisionamento Sem Fio (Improv Wi-Fi)
Este projeto inclui **Improv Wi-Fi via BLE e Serial**. Caso nenhuma credencial de Wi-Fi seja gravada durante a compilação, você pode configurar a rede sem fio:
* **Android:** Uma notificação nativa aparecerá na tela do celular para configurar o dispositivo próximo.
* **Navegador:** Acesse [web.esphome.io](https://esphome.io) usando o Chrome ou Edge e conecte via Bluetooth ou USB.
* **Segurança:** Para o pareamento Bluetooth, você deve **pressionar fisicamente o botão BOOT (GPIO0)** na placa para autorizar a conexão.

### Requisitos
* ESPHome versão `2026.5.3` ou mais recente.
* Um arquivo `secrets.yaml` no mesmo diretório contendo `wifi_ssid` e `wifi_password`.
