# Atividade ponderada 2 de Computação | Semáforo

Estudante: Nataly de Souza Cunha | T11 | G04

Professor(a): <a href="https://www.linkedin.com/in/kizzyterra/">Profª Kizzy Terra</a> 

## 🎯 Atividade

&nbsp;&nbsp;&nbsp;&nbsp;Realização de um circuito arduíno que simula o funcionamento de um semáforo

## Materiais:

| Material  | Quantidade | Especificação
| ------------- | ------------- | ------------- |
| Arduíno UNO  | 1  | - |
| LED  | 1  | Vermelho |
| LED  | 1  | Amarelo |
| LED  | 1  | Verde |
| Jumper  | Variada  | Macho-macho |
| Jumper  | 6  | Macho-fêmea |
| Jumper  | 8  | Macho-macho |
| Resistor  | 3  | 330 Ω |
| Resistor  | 1  | 10KΩ |
| Botão  | 1  | - |
| Fita isolante  | 10cm  | - |

# Parte 1 - Semáforo

&emsp;Para a realização da atividade, foram revisadas as instruções no seguinte [slide](https://drive.google.com/drive/u/0/folders/1HwvxIvuR8VfLJEdR9Q9LR64mkZmjrwcX). Como forma de "ir-além", foi escolhida a inclusão de um botão que iniciava o circuito, e logo depois foram feitas pesquisas no Google sobre semáforos com Arduíno com acionamento por botão para estudo de exemplos.
&emsp;Assim, foi sendo desenvolvido o código através do Arduíno IDE e a montagem diretamente física.


### Código

```c++
// Definindo os pinos dos LEDs e do botão
int vermelho = 10;
int amarelo = 9;
int verde = 8;
int botao = 12;

// Variável para controlar o estado do semáforo
bool semaforoLigado = false;

void setup() {
  // Configuração dos pinos como saídas e entrada para o botão
  pinMode(vermelho, OUTPUT);
  pinMode(amarelo, OUTPUT);
  pinMode(verde, OUTPUT);
  pinMode(botao, INPUT);

  // Iniciar com todos os LEDs desligados
  digitalWrite(vermelho, LOW);
  digitalWrite(amarelo, LOW);
  digitalWrite(verde, LOW);
}

void loop() {
  // Checa se o botão foi pressionado
  if (digitalRead(botao) == HIGH) {
    delay(200);  // debounce
    semaforoLigado = !semaforoLigado;  // Alterna o estado do semáforo
    while (digitalRead(botao) == HIGH);  // Aguarda o botão ser solto
  }

  // Se o semáforo está ligado, inicia o ciclo
  if (semaforoLigado) {
    semaforo();  // Executa o ciclo do semáforo
  } else {
    // Se desligado, todos os LEDs ficam apagados
    digitalWrite(vermelho, LOW);
    digitalWrite(amarelo, LOW);
    digitalWrite(verde, LOW);
  }
}

void semaforo() {
  // Etapa 1: Luz Vermelha (6 segundos)
  if (!semaforoLigado) return;
  digitalWrite(vermelho, HIGH);
  digitalWrite(amarelo, LOW);
  digitalWrite(verde, LOW);
  delay(6000);

  // Etapa 2: Luz Amarela (2 segundos)
  if (!semaforoLigado) return;
  digitalWrite(vermelho, LOW);
  digitalWrite(amarelo, HIGH);
  delay(2000);

  // Etapa 3: Luz Verde (2 + 2 segundos para pedestres)
  if (!semaforoLigado) return;
  digitalWrite(amarelo, LOW);
  digitalWrite(verde, HIGH);
  delay(4000);

  // Etapa 4: Luz Amarela (2 segundos)
  if (!semaforoLigado) return;
  digitalWrite(verde, LOW);
  digitalWrite(amarelo, HIGH);
  delay(2000);
}

```

# Circuito e execução
![20241029_140353](https://github.com/user-attachments/assets/adbc5bce-2799-4043-ac20-129393bd7cef)

![20241029_140334](https://github.com/user-attachments/assets/3f6eedaa-9258-4c30-af14-b6165b378b40)

![20241029_140341](https://github.com/user-attachments/assets/3af71eee-c250-4c7d-9963-8b1a0cfc5a97)

https://github.com/user-attachments/assets/4990387d-92a6-46fd-89dd-344a505cef36


# Circuito e execução

### Avaliador: Heitor de Faria Cândido

| Critério                                                                                                 | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|---------------------------------------------------------------------------------------------------------|--------------------|----------------------------------|--------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores                | Até 3              | Até 1,5                            | 0                        | 3                          |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo                  | Até 3              | Até 1,5                          | 0                        | 3                          |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3              | Até 1,5                          | 0                        | 3                          |
| Extra: Implmeentou um componente de liga/desliga no semáforo e/ou usou ponteiros no código | Até 1              |  Até 0,5                         | 0                        | 1                          |
|  |                                                             |  | |**Pontuação Total**|

### Avaliador: João Victor de Souza Campos

| Critério                                                                                                 | Contempla (Pontos) | Contempla Parcialmente (Pontos) | Não Contempla (Pontos) | Observações do Avaliador |
|---------------------------------------------------------------------------------------------------------|--------------------|----------------------------------|--------------------------|---------------------------|
| Montagem física com cores corretas, boa disposição dos fios e uso adequado de resistores                | Até 3              | Até 1,5                            | 0                        | 3                          |
| Temporização adequada conforme tempos medidos com auxílio de algum instrumento externo                  | Até 3              | Até 1,5                          | 0                        | 3                          |
| Código implementa corretamente as fases do semáforo e estrutura do código (variáveis representativas e comentários) | Até 3              | Até 1,5                          | 0                        | 3                          |
| Extra: Implmeentou um componente de liga/desliga no semáforo e/ou usou ponteiros no código | Até 1              |  Até 0,5                         | 0                        | 1                          |
|  |                                                             |  | |**Pontuação Total**|

