# GS IoT: Cubo de Bem-Estar (Plataforma Elysium)

Este repositório contém o código-fonte (`sketch_ino`) e a documentação para o entregável de IoT da Global Solution 2025 (FIAP).

Este protótipo, o "Cubo de Bem-Estar", é um componente central da nossa plataforma de bem-estar gamificada "Elysium", alinhada à ideia central do grupo.

## 1. O Problema Abordado


No "Futuro do Trabalho", o modelo híbrido e remoto aumentou os casos de *burnout* e a desconexão da equipe. A saúde mental dos funcionários tornou-se um desafio crítico, mas silencioso. Faltam ferramentas fáceis, físicas e de baixa fricção que incentivem o autocuidado diário, focando no tema de **"Saúde e bem-estar no trabalho"**.

## 2. A Solução Proposta


O "Cubo de Bem-Estar" é uma solução inovadora simulada no **Wokwi** que fica na mesa do funcionário. Ele permite ao funcionário fazer um "check-in" de humor de forma rápida, física e tangível.

Ao invés de precisar abrir um app, o funcionário apenas toca em um dos três **sensores** (botões Verde, Amarelo ou Vermelho). O Cubo então envia essa informação via **HTTP** para a API central da plataforma. Como feedback de sucesso, o **atuador** (o LED RGB) pisca na cor correspondente.

## 3. Simulação (Link do Wokwi)


O projeto pode ser acessado e testado em tempo real no simulador Wokwi:

**Link da Simulação:** (https://wokwi.com/projects/447468384986344449)

## 4. Funcionamento Técnico e Comunicação


O projeto utiliza um **ESP32** e, conforme o requisito "comunicação via MQTT **e/ou** HTTP", optamos por focar 100% no **HTTP** para esta demonstração, provando o envio de dados dos sensores.

* **Endpoint (Saída):** O ESP32 envia os dados do check-in para este endpoint (um Webhook de teste que simula nossa API).
* **URL:** `https://webhook.site/a2e6670b-84c2-4dfd-b569-49fddf1c9e51`
* **Método:** `POST`
* **Payload (JSON):** `{"mood":"BEM"}`, `{"mood":"OK"}` ou `{"mood":"ESTRESSADO"}`

## 5. Hardware e Dependências


### Hardware (Simulado no Wokwi)
* 1x ESP32
* 3x Botões (Sensores)
* 1x LED RGB (Atuador)

### Software (Bibliotecas Arduino)
* `WiFi.h`
* `HTTPClient.h`

## 6. Instruções de Uso e Teste


Para testar o protótipo e validar as entregas (Sensor, Atuador e HTTP):

1.  **Abra o Link da Simulação Wokwi** (listado na Seção 3).
2.  **Abra o Link do Webhook** para ver os dados chegando em tempo real: `https://webhook.site/a2e6670b-84c2-4dfd-b569-49fddf1c9e51`
3.  No Wokwi, clique no botão verde ▶ **(Play)** para iniciar a simulação.
4.  Clique em um dos botões (ex: o botão verde **"BEM"**).
5.  **Observe o Atuador:** O LED RGB no Wokwi irá piscar na cor **Verde** (ou Amarelo/Vermelho, dependendo do botão), confirmando o envio.
6.  **Observe o Webhook:** Na aba do Webhook, você verá a requisição HTTP `POST` chegando com o JSON `{"mood":"BEM"}`, provando a leitura do sensor e a comunicação HTTP.
