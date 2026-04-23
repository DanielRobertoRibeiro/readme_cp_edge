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
- Linguagem C e C++ (Arduino Framework)
- Simulador: Tinkercad 

## 🚀 Instruções de Reprodução
1. **Montagem do Hardware:** - Conecte o LDR à porta analógica `A0`.
   - Conecte os LEDs Verde, Amarelo e Vermelho às portas digitais `10`, `11` e `12` respectivamente.
   - Conecte o Buzzer à porta digital `13`.
2. **Configuração do Código:** - Clone este repositório ou copie o código fonte.
   - Ajuste os limiares de luminosidade nas variáveis de controle, se necessário, de acordo com o ambiente.
3. **Execução:** - Carregue o código no Arduino.
   - Abra o Monitor Serial para acompanhar as leituras em tempo real.
## Código Utilizado:

// Sistema de monitoramento de luminosidade - Vinheria Agnello
// LDR -> A0
// LED Verde -> pino 10
// LED Amarelo -> pino 11
// LED Vermelho -> pino 12
// Buzzer -> pino 13

int ldr = A0;

int ledVerde = 10;
int ledAmarelo = 11;
int ledVermelho = 12;
int buzzer = 13;

int valorLDR = 0;

//LIMITES
int nivelVerde = 250;
int nivelAmarelo = 590;


int leituraSuave()
{
    int soma = 0;

    for (int i = 0; i < 10; i++)
    {
        soma += analogRead(ldr);
        delay(5);
    }

    return soma / 10;
}

void setup()
{
    pinMode(ledVerde, OUTPUT);
    pinMode(ledAmarelo, OUTPUT);
    pinMode(ledVermelho, OUTPUT);
    pinMode(buzzer, OUTPUT);

    Serial.begin(9600);
}

void loop()
{
    // leitura com filtro
    valorLDR = leituraSuave();

    Serial.println(valorLDR);

  
    if (valorLDR <= nivelVerde)
    {
        digitalWrite(ledVerde, HIGH);
        digitalWrite(ledAmarelo, LOW);
        digitalWrite(ledVermelho, LOW);

        noTone(buzzer);
    }

 
    else if (valorLDR <= nivelAmarelo)
    {
        digitalWrite(ledVerde, LOW);
        digitalWrite(ledAmarelo, HIGH);
        digitalWrite(ledVermelho, LOW);

       
        delay(200);
       
        delay(500);
    }

    
    else
    {
        digitalWrite(ledVerde, LOW);
        digitalWrite(ledAmarelo, LOW);
        digitalWrite(ledVermelho, HIGH);

        tone(buzzer, 1000);
        delay(300);
        noTone(buzzer);
        delay(300);
    }

    delay(200);
}
