# Sistema de Monitoramento de Luminosidade - Vinheria Agnello 🍷

## 📝 Descrição do Projeto
Este projeto foi desenvolvido para atender às necessidades da Vinheria Agnello, focando na preservação da qualidade dos vinhos através do monitoramento constante da luminosidade ambiente. Utilizando um sistema baseado em Arduino e um sensor LDR (Fotorresistor), o dispositivo categoriza a incidência de luz em três níveis (Adequado, Alerta e Crítico), fornecendo feedback visual e sonoro imediato.

## ⚙️ Funcionalidades
- **Verde (Condições Adequadas):** Luminosidade dentro dos padrões ideais para conservação.
- **Amarelo (Nível de Alerta):** Luminosidade acima do desejado; requer atenção.
- **Vermelho (Condição Crítica):** Alerta máximo. O sistema ativa um LED vermelho e um Buzzer sonoro por 3 segundos para indicar risco imediato à integridade do produto.

## 🛠️ Componentes e Dependências
Para reproduzir este projeto, foram utilizados:
- 1x Arduino Uno R3
- 1x Sensor de Luz LDR
- 1x Resistor de 10kΩ (para o divisor de tensão do LDR)
- 3x LEDs (Verde, Amarelo, Vermelho)
- 3x Resistores de 220Ω (para os LEDs)
- 1x Buzzer (Piezo)
- Protoboard e Jumpers

**Software:**
- Linguagem C++ (Arduino Framework)
- Simulador: Tinkercad ou Wokwi

## 🚀 Instruções de Reprodução
1. **Montagem do Hardware:** - Conecte o LDR à porta analógica `A0`.
   - Conecte os LEDs Verde, Amarelo e Vermelho às portas digitais `10`, `11` e `12` respectivamente.
   - Conecte o Buzzer à porta digital `13`.
2. **Configuração do Código:** - Clone este repositório ou copie o código fonte.
   - Ajuste os limiares de luminosidade nas variáveis de controle, se necessário, de acordo com o ambiente.
3. **Execução:** - Carregue o código no Arduino.
   - Abra o Monitor Serial para acompanhar as leituras em tempo real.