# **PowerNow**

## **1. Introdução**

O mercado de energia solar no Brasil está em ascensão, consolidando-se como uma das fontes mais promissoras da matriz energética nacional. Dados recentes indicam que o país atingiu **44 GW** de capacidade instalada no primeiro semestre de 2024, tornando a energia solar a segunda maior fonte elétrica brasileira. 

Inspirados nesse crescimento, desenvolvemos o **PowerNow**, uma solução que alia tecnologia e sustentabilidade para maximizar a eficiência da energia solar. O sistema utiliza o ESP32 para monitorar e simular condições de captação solar, integrando esses dados à plataforma **Thinger.io**. Além disso, temos planos de criar um aplicativo com inteligência artificial para previsões otimizadas e sugestões personalizadas.

---
## Integrantes

- **Breno Giacoppini Câmara** - RM98695
- **Jaqueline Martins dos Santos** - RM551744
- **Mariana Bastos Esteves** - RM97510
- **Matheus Oliveira Macedo** - RM551155
- **Victor Freitas Silva** - RM99982

---
## Demonstração em Vídeo

Assista à demonstração no YouTube: 

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

## **4. Exemplo de Cálculo Real**

### **Irradiação Solar (0.87 kW/m²)**

Este valor representa a energia solar incidente por metro quadrado em um determinado momento. Uma irradiância de 0.87 kW/m² é razoável para um dia ensolarado ou parcialmente nublado, dependendo da localização e da hora do dia. O valor máximo teórico de irradiância solar direta é cerca de 1 kW/m².

### **Eficiência dos Painéis Solares (16%)**

A eficiência de 16% é típica para painéis solares comerciais de boa qualidade. Este valor está dentro do intervalo usual de eficiência para tecnologias de silício cristalino (geralmente entre 15% e 22%).

### **Energia Gerada (0.56 kWh)**

O cálculo da energia gerada foi feito com base na fórmula:


![Formula 1](https://github.com/user-attachments/assets/2ca44bb3-26ae-4457-b25a-c80722f1e14e)


No seu caso, a área considerada implicitamente foi 1 m² e as horas de pico solar foram fixadas em 4 horas.

Substituindo os valores:


![Formula 2](https://github.com/user-attachments/assets/69ca8334-b250-4721-9932-4c9c844a1935)


O valor resultante de **0.56 kWh** está correto e é coerente com as condições simuladas.

### **Interpretação**

Esse painel solar hipotético (de 1 m²) geraria aproximadamente **0.56 kWh** em um dia com 4 horas de pico solar sob essas condições. Em uma instalação maior, com mais painéis, a energia gerada seria proporcional à área de captura solar.

### **Vantagem de 0.56 kWh**

A vantagem de gerar **0.56 kWh** com 1 m² de painel solar é significativa, especialmente para residências ou pequenas empresas. Este valor de energia pode ser utilizado para abastecer uma parte da carga elétrica de um imóvel, como iluminação, carregamento de dispositivos eletrônicos, ou até mesmo para reduzir o consumo da rede elétrica. A vantagem está na redução de custos com energia elétrica e na contribuição para um ambiente mais sustentável, visto que a energia solar é renovável e limpa. Além disso, esse valor representa a eficiência do painel solar, que, dependendo das condições climáticas e da instalação, pode ser otimizado ao longo do tempo com tecnologias mais avançadas.

### **Conclusão**

Sim, os valores simulados de **0.56 kWh** são consistentes com condições reais para a irradiância e eficiência de painéis solares comerciais. A simulação oferece uma visão prática do desempenho de sistemas solares, possibilitando o planejamento e a tomada de decisões informadas sobre o uso de energia solar em diferentes contextos.

---

## **5. Inovação**

O **PowerNow** se destaca por integrar IoT e simulações realistas, com planos para incluir IA no futuro:

- **Monitoramento em Tempo Real:** Dados enviados diretamente ao **Thinger.io**.
- **Simulação Educativa:** Usuários podem explorar fatores que afetam a geração de energia.
- **Projeções Futuras com IA:** Previsões baseadas em dados climáticos e geográficos.

---

## **6. Usabilidade**

- **Configuração Intuitiva:**  
  Instalação e configuração do ESP32 são diretas, mesmo para iniciantes.

- **Visualização Interativa:**  
  Dados simulados são exibidos de forma clara no **Thinger.io**, permitindo análise em tempo real.

- **Expansão Futura:**  
  Planejamento para integrar funcionalidades avançadas via aplicativo.

---

## **7. Benefícios**

- **Econômicos:**  
  - Redução de custos com otimização do sistema.  
  - Estímulo ao uso consciente de energia.

- **Ambientais:**  
  - Incentivo ao uso de fontes renováveis.  
  - Contribuição para redução das emissões de carbono.

---

## **8. Conclusão**

O **PowerNow** é uma solução inovadora que combina tecnologia e sustentabilidade para atender à crescente demanda por energia limpa no Brasil. Ao utilizar IoT e planejar a integração de IA, o projeto se posiciona como uma ferramenta essencial para maximizar o aproveitamento de energia solar.

 
