# Controle de LED Onboard e Publicação MQTT

## Integrantes Nextfutre:
**Geronimo Augusto**: 557170
**Ana Laura**: 554375
**Murilo Cordeiro**: 556727
**Vitor Augusto**: 555469

## Descrição
Este projeto controla o LED onboard de um ESP32 e envia o status do LED (ligado ou desligado) para um broker MQTT. Além disso, o código realiza a leitura do sensor de luminosidade e publica os valores de luminosidade em um tópico específico do broker MQTT.

Este código foi ajustado para funcionar no ambiente **FIWARE Descomplicado**, utilizando o broker MQTT da Azure para integração.

## Funcionalidades
1. **Conexão Wi-Fi**: O ESP32 conecta-se a uma rede Wi-Fi especificada.
2. **Publicação e Assinatura MQTT**:
   - Publica o estado do LED (ligado/desligado) em um tópico MQTT.
   - Publica o valor da luminosidade lida pelo sensor no tópico MQTT.
   - Assina um tópico MQTT para receber comandos de ligar/desligar o LED.
3. **Leitura de Luminosidade**: O ESP32 realiza a leitura do valor de luminosidade (usando um potenciômetro como sensor de luminosidade) e envia os dados ao broker.

## Estrutura do Projeto
### Principais Arquivos e Funções
- **setup()**: Inicializa o LED, a comunicação serial, a conexão Wi-Fi, e a comunicação com o broker MQTT.
- **loop()**: Verifica as conexões Wi-Fi e MQTT, envia o estado do LED ao broker, lê o sensor de luminosidade e publica o valor no MQTT.
- **mqtt_callback()**: Função de callback que recebe mensagens MQTT para controlar o estado do LED.
- **handleLuminosity()**: Lê o valor do sensor de luminosidade e publica no broker MQTT.

## Configurações
Você pode personalizar as seguintes variáveis:
- **Rede Wi-Fi**:
  - SSID: `FIAP-IBM`
  - Senha: `Challenge@24!`
- **Broker MQTT**:
  - IP: `O ip do seu servidor`
  - Porta: `1883`
  - Tópico de comando: `/TEF/lamp051/cmd`
  - Tópico de envio de estado: `/TEF/lamp051/attrs`
  - Tópico de envio de luminosidade: `/TEF/lamp051/attrs/l`
  - ID MQTT: `fiware_051`

## Dependências
Para rodar este código, você precisa das seguintes bibliotecas:
- **WiFi.h**: Biblioteca padrão para conexão Wi-Fi.
- **PubSubClient.h**: Biblioteca para comunicação MQTT.

## Instruções de Uso
1. Clone o projeto ou copie o código para o seu ambiente de desenvolvimento Arduino.
2. Configure as credenciais de rede Wi-Fi e as informações do broker MQTT no código.
3. Faça o upload para o ESP32.
4. Verifique a saída no monitor serial para acompanhar o processo de conexão e envio de dados.

## Observações
- O código já está configurado para funcionar com o FIWARE Descomplicado.
- Certifique-se de que o broker MQTT esteja em funcionamento e acessível.
- O LED começa desligado por padrão ao iniciar o dispositivo.

## Melhorias Futuras
- Implementar mais sensores ou atuadores.
- Adicionar suporte para mais protocolos de comunicação.
