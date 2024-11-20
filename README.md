# **PowerNow**

## **1. Introdução**

O mercado de energia solar no Brasil está em ascensão, consolidando-se como uma das fontes mais promissoras da matriz energética nacional. Dados recentes indicam que o país atingiu **44 GW** de capacidade instalada no primeiro semestre de 2024, tornando a energia solar a segunda maior fonte elétrica brasileira. 

Inspirados nesse crescimento, desenvolvemos o **PowerNow**, uma solução que alia tecnologia e sustentabilidade para maximizar a eficiência da energia solar. O sistema utiliza o ESP32 para monitorar e simular condições de captação solar, integrando esses dados à plataforma **Thinger.io**. Além disso, temos planos de criar um aplicativo com inteligência artificial para previsões otimizadas e sugestões personalizadas.

---

## **2. Objetivo**

O **PowerNow** tem como principais objetivos:

- Monitorar e analisar, em tempo real, a eficiência de painéis solares.
- Simular cenários de geração de energia para educar e engajar usuários.
- Incentivar o uso da energia solar, destacando benefícios econômicos e ambientais.
- Criar uma base sólida para integração futura com IA, possibilitando previsões personalizadas de geração e uso de energia.

---

## **3. Funcionamento Técnico**

### **3.1. Preparação e Configuração da IDE Arduino**

Para começar a utilizar o **PowerNow**, siga as instruções abaixo:

1. **Baixe e Instale a IDE Arduino:**
   - Acesse o [site oficial do Arduino](https://www.arduino.cc) e baixe a versão apropriada para o seu sistema operacional.
   - Instale a IDE seguindo as orientações.

2. **Adicione a Placa ESP32:**
   - Na IDE Arduino, vá em **Arquivo > Preferências**.
   - No campo **URLs Adicionais para Gerenciadores de Placas**, insira:  
     `https://dl.espressif.com/dl/package_esp32_index.json`.
   - Em **Ferramentas > Placa > Gerenciador de Placas**, procure por "ESP32" e clique em **Instalar**.

3. **Instale as Bibliotecas Necessárias:**
   - Acesse **Ferramentas > Gerenciar Bibliotecas**.
   - Pesquise e instale:
     - `WiFi.h` (já integrada com ESP32).
     - `ThingerESP32` (para integração com o **Thinger.io**).

---

### **3.2. Estrutura do Código**

O código é dividido em partes organizadas para facilitar a compreensão e manutenção:

1. **Definições e Credenciais:**
   - Configuração de bibliotecas, credenciais do dispositivo no **Thinger.io** e credenciais de Wi-Fi.

2. **Configuração Inicial (setup):**
   - Conexão à rede Wi-Fi.
   - Integração com o **Thinger.io** para enviar dados.
   - Inicialização da simulação.

3. **Loop Principal (loop):**
   - Atualização periódica de variáveis simuladas.
   - Comunicação contínua com o **Thinger.io**.
   - Intervalos entre atualizações com uso de `delay()`.

4. **Função de Simulação (gerarSimulacao):**
   - Geração de valores aleatórios para variáveis-chave.
   - Cálculo de energia gerada com base em irradiância e eficiência.

---

### **3.3. Funções Importantes**

- **thing.add_wifi(ssid, password):**  
  Realiza a conexão com a rede Wi-Fi usando as credenciais fornecidas.

- **thing["variavel"] >> outputValue(variavel):**  
  Permite enviar dados simulados para o painel de controle do **Thinger.io**.

- **random(min, max):**  
  Gera valores aleatórios para simulação de irradiância e eficiência.

- **Serial.print / Serial.println:**  
  Exibe os dados simulados no monitor serial para monitoramento local.

- **delay(ms):**  
  Introduz pausas entre as atualizações para evitar sobrecarga.

---

### **3.4. Explicação das Variáveis Simuladas**

O **PowerNow** simula três variáveis-chave que refletem condições típicas para sistemas solares no Brasil:

- **Irradiância Solar (kW/m²):**  
  Intervalo: 0,05 a 1,0 kW/m². Representa a intensidade da radiação solar em diferentes momentos do dia, considerando dias nublados e ensolarados.

- **Eficiência dos Painéis Solares (%):**  
  Intervalo: 15% a 22%. Esses valores são típicos para painéis comerciais, refletindo limites práticos de desempenho.

- **Energia Gerada (kWh):**  
  Calculada com base na irradiância, eficiência e 4 horas de pico solar. Esse tempo médio representa condições de insolação em regiões como o Nordeste brasileiro.

Esses intervalos foram escolhidos com base em padrões reais para garantir que as simulações sejam representativas e úteis.

---

## **4. Inovação**

O **PowerNow** se destaca por integrar IoT e simulações realistas, com planos para incluir IA no futuro:

- **Monitoramento em Tempo Real:** Dados enviados diretamente ao **Thinger.io**.
- **Simulação Educativa:** Usuários podem explorar fatores que afetam a geração de energia.
- **Projeções Futuras com IA:** Previsões baseadas em dados climáticos e geográficos.

---

## **5. Usabilidade**

- **Configuração Intuitiva:**  
  Instalação e configuração do ESP32 são diretas, mesmo para iniciantes.

- **Visualização Interativa:**  
  Dados simulados são exibidos de forma clara no **Thinger.io**, permitindo análise em tempo real.

- **Expansão Futura:**  
  Planejamento para integrar funcionalidades avançadas via aplicativo.

---

## **6. Benefícios**

- **Econômicos:**  
  - Redução de custos com otimização do sistema.  
  - Estímulo ao uso consciente de energia.

- **Ambientais:**  
  - Incentivo ao uso de fontes renováveis.  
  - Contribuição para redução das emissões de carbono.

---

## **7. Conclusão**

O **PowerNow** é uma solução inovadora que combina tecnologia e sustentabilidade para atender à crescente demanda por energia limpa no Brasil. Ao utilizar IoT e planejar a integração de IA, o projeto se posiciona como uma ferramenta essencial para maximizar os benefícios econômicos e ambientais da energia solar.
