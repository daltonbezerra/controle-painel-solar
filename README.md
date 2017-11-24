# Painel Solar Seguidor de Luz

Professor: Afonso Alves

Alunos:
Lucas Valente,
Rodrigo Lopes,
Dalton Bezerra,
Rodrigo Paulo


## INTRODUÇÃO
![image](https://user-images.githubusercontent.com/32208559/33126554-14244076-cf6c-11e7-810a-064e7f2e85b9.png)

O objetivo do projeto é construir um painel solar que permita tanto o controle manual quanto o controle automático do mesmo. Para isso, utilizaremos um botão para definir o modo de controle que iremos utilizar.

Para o controle manual, utilizaremos dois potenciometros. A medida que giramos os potenciometros, os servo motores também giram.

Já para o controle automático, utilizaremos quatro LDRs (Resistor dependente de luz, da sigla em inglês), que controlarão o atuador dependendo da intensidade da luz atuando em cada um deles.

Para isso, precisaremos dos seguintes componentes eletrônicos:

- Atuadores:
Servo motor de um eixo (02)

- Sensores:
LDR (04)

- Controladores:
Potenciometro (02),
Arduino Uno

- Material Restante:
Protoboard (01),
Botão (01),
Resistor de 1k (06),
Cabos,
LED (01)



## IMPLEMENTAÇÃO


- O LDR funciona da seguinte maneira, quanto maior a luminosidade incidente no LDR, mais o servo motor se moverá na direção do LDR. Essa movimentação ocorrerá até que todos os LDRs estejam com o mesmo percentual de iluminação.


![image](https://user-images.githubusercontent.com/32208559/33126678-763aaf20-cf6c-11e7-81c9-d140fa7f24d6.png)



- O potenciometro é um componente elétrico que possui uma resistência ajustável. Seu valor resistivo foi atrelado a uma variável que representa quantos graus o servo motor irá girar, ou seja, a medida que giramos o potenciometro, sua resistencia aumenta, fazendo com que a variável atrelada a ele sofra mudanças em seus valores e faça o servo motor rotacionar.


![image](https://user-images.githubusercontent.com/32208559/33126721-aad35976-cf6c-11e7-9387-fb871d73f64b.png)



- O servo motor é o atuador, é essa peça que recebe os sinais e executa os comandos.


![image](https://user-images.githubusercontent.com/32208559/33126737-bead136a-cf6c-11e7-9351-65c6e30d1d20.png)



- A Finalidade dos resistores é apenas limitar as correntes que atuam no circuito.


![image](https://user-images.githubusercontent.com/32208559/33126751-d217aec4-cf6c-11e7-80cd-b257a3ec822d.png)



- A protoboard assim como os cabos, são os componentes utilizados para fazer a montagem e interligação de todos os outros componentes do projeto.


![image](https://user-images.githubusercontent.com/32208559/33126767-e1f50062-cf6c-11e7-962e-4e1f1b5811d2.png)



- A Finalidade do botão neste projeto é apenas selecionar o tipo de controle que iremos utilizar no painel solar, se é manual (potenciometros), ou automático (LDRs).


![image](https://user-images.githubusercontent.com/32208559/33126786-f4aa815a-cf6c-11e7-9fdb-70167ade546e.png)



- O arduino Uno é a plataforma utilizada para o desenvolvimento do projeto, ele é responsável pela prototipagem, implementação e emulação dos controle de sistemas interativos.


![image](https://user-images.githubusercontent.com/32208559/33126799-084ab392-cf6d-11e7-86f8-86e5754f8154.png)



- O LED é um diodo emissor de luz, da sigla em inglês LED. SUa função neste projeto é indicar caso o controle automatico tenha sido ativado.


![image](https://user-images.githubusercontent.com/32208559/33126819-1c6cfaba-cf6d-11e7-9218-a96aeddf1ee6.png)




## FLUXOGRAMA

 
  ![image](https://user-images.githubusercontent.com/32208559/33126381-6bbd47f2-cf6b-11e7-8340-d3f78960ac3e.png)
          Aqui nós temos um fluxograma de como o código de fato funciona, a partir do momento que alimentamos o arduino, ele já entra na declaração de variáveis e após isso, ele vai para o modo de seleção de controle.
          O que é o modo de seleção de controle? Nada mais é do que informar para o arduino se vamor querer controlar o painel de modo manual (utilizando potenciometros), ou de modo automático (utilizando os LDRs).
          Após a seleção do modo de controle, ocorre a execução do código.


## DIAGRAMA DE BLOCOS


   ![whatsapp image 2017-11-21 at 21 28 22](https://user-images.githubusercontent.com/32208559/33126487-d15af262-cf6b-11e7-9938-c9dfa28f55dd.jpeg)
          Esse é o diagrama de blocos de malha fechada, ele ilustra o que acontece com o sistema quando estamos operando no modo automático, ou seja, utilizando os LDRs. O input inicial é um valor já definido na declaração de variáveis do código. O arduino atua com esse valor em cima dos servo motores e após a primeira interação, os LDRs começão a realimentar o sistema mudando esse input a cada ciclo.



## ESQUEMÁTICO

![image](https://user-images.githubusercontent.com/32208559/33126554-14244076-cf6c-11e7-810a-064e7f2e85b9.png)
          Como no projeto real é muito mais complicado de se entender visualmente as ligações, nós criamos esse esquemático através do TinkerCad para facilitar a visualição e compreensão de como fazer as ligações no arduino.


# O CÓDIGO


#### Inclui a livraria dos servo motores e declara todas as variáveis que serão utilizadas ao longo do código, bem como todas portas nas quais estão conectados cada componente.

 #include <Servo.h>

 Servo meuservo1;

 Servo meuservo2;

 int LDR1 = A5;

 int LDR2 = A4;

 int LDR3 = A0;

 int LDR4 = A1;

 int pos1 = 90;

 int pos2 = 90;

 int pot1 = A2;

 int pot2 = A3;

 int led = 0;

 int botao = 5;

 int var = LOW;


#### Esse bloco do código declara o LED como componente de saída e o botão como entrada. Além disso, informa em quais portas digitais estão conectados cada servo e define qual variável irá representar a rotação de cada servo.

void setup(){

  pinMode(led, OUTPUT);
  
  pinMode(botao, INPUT);
  
  digitalWrite(led,0);
  
  meuservo1.attach(2);
  
  meuservo2.attach(4);
  
  meuservo1.write(pos1);
  
  meuservo2.write(pos2);
  
}


#### Esse pequeno bloco de código lê caso o botão seja pressionado.
#### Por padrão, o programa começa a rodar no modo manual, caso o botão seja pressionado ele passa a rodar no modo automático.

void loop(){

  int press = digitalRead(botao);
  
  if (press == 1){
  
   var =1-var;
   
  }


#### Este bloco representa o modo manual de operação. Nesse bloco o arduino lê o valor associado aos potenciômetros, os converte em graus e escreve o valor em seu respectivo servo motor.

#### modo manual
  if (var == 0){
  
  digitalWrite(led,var);
  
    int leiturapot1 = analogRead(pot1);
    
    int leiturapot2 = analogRead(pot2);
    
    int graus1 = map(leiturapot1, 0, 1023, 0, 180);
    
    int graus2 = map(leiturapot2, 0, 1023, 0, 180);
    
    meuservo1.write(graus1);
    
    meuservo2.write(graus2);
    
  }
  
#### Este bloco do código representa ao modo automático de operação. O arduíno entrará nesta parte do código caso o botão seja pressionado.

#### Quando o programa está em modo automático, o LED é ligado.

#### Nesse bloco de código acontece a leitura de cada um dos LDR e a conversão dos mesmos para variáveis que representam a porcentagem de luz incidente em cada um deles.

#### modo automatico
  if (var == 1){
  
  digitalWrite(led,var);
  
  int leitura1 = analogRead(LDR1);
  
  int leitura2 = analogRead(LDR2);
  
  int leitura3 = analogRead(LDR3);
  
  int leitura4 = analogRead(LDR4);
  

  int graus1 = map(leitura1, 1017,344,0,100);
  
  int graus2 = map(leitura2, 1017,344,0,100);
  
  int graus3 = map(leitura3, 1017,344,0,100);
  
  int graus4 = map(leitura4, 1017,344,0,100);






#### Neste próximo bloco do código, ocorre a comparação da incidência de luz em cada LDR.
#### A comparação é necessária pois é através dela que definiremos para qual lado o servo motor deverá rotacionar.
 
  if (graus1>graus2){
  
    pos1 = pos1+1;
    
    meuservo1.write(pos1);
    
    if (pos1>179){
    
      pos1=180; }
      
  }
  
  else if(graus1<graus2) {
  
    pos1 = pos1-1;
    
    meuservo1.write(pos1);
    
    if (pos1<1){
    
      pos1=0;}
      
  }
  
  if (graus3>graus4){
  
    pos2 = pos2+1;
    
    meuservo2.write(pos2);
    
    if (pos2>179){
    
      pos2=180; }
      
  }
  else if(graus3<graus4) {
  
    pos2 = pos2-1;
    
    meuservo2.write(pos2);
    
    if (pos2<1){
    
      pos2=0;}
      
  }
  
  }
  
  delay(200);
  
}

## CONCLUSÃO


A principal aplicação deste projeto é em painéis fotovoltaicos de usinas de energia solar. Este sistema possibilita um aproveitamento muito maior na conversão de energia fotovoltaica uma vez que os painéis solares estariam sempre voltados em direção ao sol.
Para que essa implementação ocorra, será necessário otimizar o código, pesquisar por componentes mais resistentes a intempéries já que os mesmos ficariam expostos no campo, fabricar o produto em escala industrial.


