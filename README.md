
# ClearVolt - Sistema Automático de Limpeza de Placas Solares

## Descrição do Projeto

O **ClearVolt** é um sistema automatizado para limpeza de placas solares
que monitora as condições ambientais e atua conforme a necessidade para
maximizar a eficiência energética.
O projeto utiliza sensores para medir temperatura e umidade, simulando
ações de limpeza como jatos de água e ar, representados por LEDs.
O sistema também se conecta à internet para enviar os dados ambientais
ao **ThingSpeak**, permitindo o acompanhamento remoto das condições.

O projeto foi desenvolvido para ser executado no simulador **Wokwi**,
 mas também pode ser adaptado para aplicações no mundo real.

---

## Link para o vídeo no youtube: 

---

## Principais Funcionalidades

1. **Monitoramento Ambiental:**
   - Leitura de temperatura e umidade utilizando o sensor **DHT22**.

2. **Ação Condicional:**
   - **Jato de Água (LED_WATER):** Ativado quando a temperatura ultrapassa 35°C.
   - **Jato de Ar (LED_AIR):** Ativado quando a umidade está abaixo de 30%.

3. **Conectividade:**
   - Conexão WiFi para enviar os dados de temperatura e umidade para a plataforma **ThingSpeak**.

4. **Simulação Visual:**
   - LEDs representam os mecanismos de limpeza (jatos de água e ar).

---

## Hardware Utilizado

- **DHT22** (ou **DHT11**) - Sensor de temperatura e umidade.
- **ESP32** - Microcontrolador para processamento e conectividade WiFi.
- **LEDs** - Indicadores para simulação das ações de limpeza.
- Resistores de 220Ω (para proteção dos LEDs).

---

## Diagrama de Conexão

| Componente        | Pino ESP32     |
|--------------------|----------------|
| DHT22 (VCC)       | 3.3V          |
| DHT22 (GND)       | GND           |
| DHT22 (DATA)      | GPIO4         |
| LED_WATER (Anodo) | GPIO15        |
| LED_AIR (Anodo)   | GPIO16        |
| LEDs (Catodo)     | GND (via resistor de 220Ω) |

---

## Instruções para Reproduzir e Testar

### 1. **Configuração do Ambiente**
   - Acesse o simulador [Wokwi](https://wokwi.com/).
   - Crie um novo projeto selecionando o microcontrolador **ESP32**.
   - Importe o código fornecido no campo de código do Wokwi.

### 2. **Adicionar Componentes no Wokwi**
   - Adicione os componentes:
     - **DHT22 Sensor**.
     - **Dois LEDs** para representar os jatos de água e ar.
   - Configure os pinos conforme o diagrama de conexão.

### 3. **Substituir as Credenciais**
   - Configure as credenciais de WiFi:
     - **SSID:** Wokwi-GUEST (ou outra rede disponível no simulador).
     - **Senha:** Deixe em branco para o Wokwi-GUEST.
   - Substitua a API Key do ThingSpeak pela sua chave gerada no painel da plataforma.

### 4. **Execução do Código**
   - Inicie a simulação no Wokwi.
   - Abra o **Serial Monitor** para acompanhar a saída.

---

## Testando as Funcionalidades

1. **Temperatura Elevada (>35°C):**
   - Modifique o valor de temperatura no sensor DHT22 para mais de 35°C.
   - O LED_WATER deve acender por 5 segundos.

2. **Umidade Baixa (<30%):**
   - Reduza o valor de umidade no sensor DHT22 para menos de 30%.
   - O LED_AIR deve acender por 5 segundos.

3. **Dados no ThingSpeak:**
   - Confirme no **Serial Monitor** que os dados estão sendo enviados.
   - Verifique os gráficos no painel do ThingSpeak.

---

## Estrutura do Código

1. **Bibliotecas Importadas:**
   - `WiFi.h`: Para conectividade WiFi.
   - `HTTPClient.h`: Para envio de dados HTTP.
   - `DHT.h`: Para leitura do sensor DHT.

2. **Configuração Inicial:**
   - Define pinos e inicializa o sensor, LEDs e conexão WiFi.

3. **Loop Principal:**
   - Lê os valores do sensor.
   - Verifica condições para acionar os LEDs.
   - Envia dados para o ThingSpeak.

4. **Conexão ThingSpeak:**
   - Envia dados de temperatura e umidade usando requisições HTTP.

---

## Exemplo de Saída no Serial Monitor

```
Conectando ao WiFi...
Conectado ao WiFi.
Sistema ClearVolt iniciado.
Temperatura: 36.2 °C, Umidade: 45.0 %
Jato de água ativado.
Dados enviados ao ThingSpeak!
Temperatura: 25.5 °C, Umidade: 28.0 %
Jato de ar ativado.
Dados enviados ao ThingSpeak!
```

---

## Integrantes da Equipe ClearVolt

- Gabriel Eduardo De Paiva Oliveira - RM: 98843
- Macirander Souza De Miranda Filho - RM: 551416
- Maria Luiza de Oliveira Lobo      - RM: 552169
- Matheus Felipe Camarinha Duarte   - RM: 552295
- Munir Jamil Mahmoud Ayoub         - RM: 555893


## Licença

Este projeto é distribuído sob a licença **MIT**, permitindo sua utilização, modificação e distribuição.

---

Para dúvidas ou sugestões, entre em contato! 😊

