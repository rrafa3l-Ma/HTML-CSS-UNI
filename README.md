📱 Sistema de Monitoramento Inteligente IoT (Energia & Água)
Aplicação Full-Stack para telemetria em tempo real de consumo elétrico (corrente) e hídrico (umidade/fluxo), integrada ao simulador ESP32 (Wokwi), com banco de dados SQLite, detecção de anomalias, projeção de consumo e exportação de relatórios.

🏗️ Arquitetura e Separação de Camadas
Hardware / Simulador (Wokwi ESP32): Coleta leituras de corrente e umidade e envia via HTTP POST em formato JSON.
Túnel Local (VS Code Dev Tunnels): Expõe a porta 5000 em HTTPS para comunicação segura com o simulador externo.
Back-end (server.js — Node.js + Express + SQLite): Recebe telemetria em /receber_dados, armazena registros com data/hora e janela deslizante (máximo de 300 registros por tabela), calcula projeções e identifica leituras acima do limite.
Front-end (public/ — HTML5, CSS3, JS + Chart.js): Interface visual desacoplada com velocímetros dinâmicos, alertas visuais de sobrecarga/vazamento, simuladores e geração de relatórios.
🚀 Instalação e Execução
Instalar dependências:
npm install express sqlite3 cors
