# Tradutor Morse para Arduino com Display OLED

Este projeto implementa um tradutor de código Morse para texto utilizando um Arduino, dois botões, um buzzer, um LED e um display OLED.

## Funcionalidades

- **Botão de Digitar (BTN_DIGITAR)**: 
  - Pressione rapidamente (<300ms) para inserir um ponto (.)
  - Mantenha pressionado (>300ms) para inserir um traço (-)
- **Botão de Enviar (BTN_ENVIAR)**: 
  - Converte a sequência Morse digitada em um caractere alfanumérico
- **Combinação de Botões (BTN_DIGITAR + BTN_ENVIAR)**:
  - Limpa todo o texto e começa uma nova tradução

## Componentes Necessários

- Arduino (qualquer modelo compatível)
- Display OLED SSD1306 (128x64 pixels)
- 2 botões push-button
- Buzzer passivo
- LED (com resistor apropriado)
- Resistores de pull-down/pull-up conforme necessário

## Esquema de Conexões

- **Display OLED**: Conectado via I2C (SDA, SCL)
- **BTN_DIGITAR**: Pino digital 2
- **BTN_ENVIAR**: Pino digital 3
- **BUZZER**: Pino digital 8
- **LED**: Pino digital 9

## Bibliotecas Requeridas

- Wire.h (para comunicação I2C)
- Adafruit_SSD1306.h (para controle do display OLED)
- Adafruit_GFX.h (para gráficos no display)

## Como Usar

1. Conecte todos os componentes conforme o esquema
2. Carregue o código no Arduino
3. O display mostrará instruções iniciais
4. Use os botões para:
   - BTN_DIGITAR: criar caracteres Morse (pontos e traços)
   - BTN_ENVIAR: finalizar um caractere e traduzir
   - Ambos juntos: limpar a tela e começar novamente

## Tabela de Tradução

O código inclui a tabela Morse padrão para:
- Letras A-Z (maiúsculas)
- Números 0-9

## Personalização

Você pode ajustar:
- `SHORT_PRESS` para alterar a sensibilidade do botão
- Tons do buzzer modificando os parâmetros da função `tone()`
- Tempos de delay conforme sua preferência

## Limitações

- Não inclui caracteres especiais ou pontuação
- Requer pausa manual entre caracteres (pressionar BTN_ENVIAR)
- Distinção entre ponto/traço baseada apenas no tempo de pressão

## Exemplo de Uso

Para digitar "SOS":
1. Pressione BTN_DIGITAR 3x rapidamente (...)
2. Pressione BTN_ENVIAR (mostrará "S")
3. Pressione BTN_DIGITAR 3x mantido (---)
4. Pressione BTN_ENVIAR (mostrará "O")
5. Pressione BTN_DIGITAR 3x rapidamente (...)
6. Pressione BTN_ENVIAR (mostrará "S")
7. Resultado final no display: "SOS"
