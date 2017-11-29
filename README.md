# Painel Solar Seguidor de Luz

Professor: Afonso Alves

Alunos:
Lucas Valente,
Rodrigo Lopes,
Dalton Bezerra,
Rodrigo Paulo


## INTRODUÇÃO
![image](https://github.com/daltonbezerra/controle-painel-solar/blob/master/WhatsApp%20Image%202017-11-24%20at%2015.24.56.jpeg)

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
          
Aqui nós temos um fluxograma de como o código de fato funciona, a partir do momento que alimentamos o arduino, ele já entra na declaração de variáveis e após isso, ele vai para o modo de seleção de controle. O que é o modo de seleção de controle? Nada mais é do que informar para o arduino se vamor querer controlar o painel de modo manual (utilizando potenciometros), ou de modo automático (utilizando os LDRs). Após a seleção do modo de controle, ocorre a execução do código.


## DIAGRAMA DE BLOCOS


   ![whatsapp image 2017-11-21 at 21 28 22](https://user-images.githubusercontent.com/32208559/33126487-d15af262-cf6b-11e7-9938-c9dfa28f55dd.jpeg)
Esse é o diagrama de blocos de malha fechada, ele ilustra o que acontece com o sistema quando estamos operando no modo automático, ou seja, utilizando os LDRs. O input inicial é um valor já definido na declaração de variáveis do código. O arduino atua com esse valor em cima dos servo motores e após a primeira interação, os LDRs começão a realimentar o sistema mudando esse input a cada ciclo.

![whatsapp image 2017-11-24 at 16 09 14](https://user-images.githubusercontent.com/32558138/33221895-deb3987a-d131-11e7-9088-d8d57c88bf06.jpeg)

Esse é o diagrama de blocos de malha aberta, ele ilustra o que acontece com o sistema quando estamos operando no modo manual, ou seja, utilizando os potenciômetros. O input inicial é um valor atual no potenciômetro. O arduino atua com esse valor em cima dos servo motores.

## ESQUEMÁTICO

![image](https://user-images.githubusercontent.com/32208559/33126554-14244076-cf6c-11e7-810a-064e7f2e85b9.png)
          
Como no projeto real é muito mais complicado de se entender visualmente as ligações, nós criamos esse esquemático através do TinkerCad para facilitar a visualição e compreensão de como fazer as ligações no arduino.


# O CÓDIGO


#### Neste trecho do código é onde nós declaramos todas as variáveis que serâo utilizadas ao longo do código. É aqui também que informamos ao arduino em que porta cada componente está conectado. Caso do LDR 1 que está conectado a porta analógica 5.

#include <Servo.h>

Servo meuservo1;

Servo meuservo2;

int LDR1 = A5;

int LDR2 = A4;

int LDR3 = A0;

int LDR4 = A1;

int pos1 = 30;

int pos2 = 30;

int pot1 = A2;

int pot2 = A3;

int led = 3;

int botao = 5;

int var = LOW;

int t_ant1=0;

int t_atual1=0;

float integral1=0;

int t_ant2=0;

int t_atual2=0;

float integral2=0;

float derivada1=0;

float derivada2=0;

int erro1=0;

int erro1_ant=0;

int derro1=0;

int erro2=0;

int erro2_ant=0;

int derro2=0;


#### No void Setup, nós informamos ao arduino que o LED é um componente de saída (OUTPUT) e o botâo é um componente de entrada (INPUT). É nesse trecho também que nós informamos que o servomotor1 está conectado a porta serial 2 e que o servomotor2 está conectado a porta serial 4.

void setup(){

  pinMode(led, OUTPUT);
  
  pinMode(botao, INPUT);
  
  digitalWrite(led,0);
  
  meuservo1.attach(2);
  
  meuservo2.attach(4);
  
#### Nesse trecho do código nós informamos ao arduino que o estado inicial dos servomotores é em 30 graus. Isso é muito importante, pois como os servomotores tem um curso total de 0 a 180 graus, porém nós decidimos que ele irá trabalhar de 0 a 60. Caso sejam iniciados em qualquer outro valor que não seja na metade ele terá menos curso para um lado do que para o outro. (Repare que na declaração de variáveis, pos1 e pos2 são iguais a 90).
  
  meuservo1.write(pos1);
  
  meuservo2.write(pos2);
  
  Serial.begin(9600);
  
}


#### Esse pequeno bloco de código lê caso o botão seja pressionado.
#### Por padrão, o programa começa a rodar no modo manual. A variável "var" é responsável por definir se ele irá para o modo manual (var = 0) ou para o modo automático (var = 1)

void loop(){

  int press = digitalRead(botao);
  
  if (press == 1){
  
   var =1-var;
   
  }


#### Este bloco representa o modo manual de operação (var = 0).

#### modo manual
  if (var == 0){
  
#### Para o modo manual de operação, o LED de indicação deve permanecer desligado, por isso:
  
  digitalWrite(led,var);
  
#### Nesta parte do código nós lemos os valores analógicos dos potenciômetros que vão de (0 a 1023) e os convertemos para (0 a 60). Após isso, escrevemos os valores já convertidos nos servomotores.
  
    int leiturapot1 = analogRead(pot1);
    
    int leiturapot2 = analogRead(pot2);
    
    int graus1 = map(leiturapot1, 0, 1023, 0, 60);
    
    int graus2 = map(leiturapot2, 0, 1023, 0, 60);
    
    meuservo1.write(graus1);
    
    meuservo2.write(graus2);
    
  }
  
#### Este bloco do código representa ao modo automático de operação. O arduíno entrará nesta parte do código caso o botão seja pressionado e a variável (var = 1).

  if (var == 1){
  
  #### Quando o programa está em modo automático, o LED é ligado.
  
 digitalWrite(led,var);
 
 #### Nesse bloco de código acontece a leitura de cada um dos LDR que vai de (1017 quando está totalmente escuro até 344 quando está totalmente claro).  Após a leitura, ocorre a conversão dos mesmos para variáveis que representam a porcentagem (0 para totalmente escuro e 100 para totalmente claro).
 
 int leitura1 = analogRead(LDR1);
 
 int leitura2 = analogRead(LDR2);
 
 int leitura3 = analogRead(LDR3);
 
 int leitura4 = analogRead(LDR4);
 
 int graus1 = map(leitura1, 1017,344,0,100);
 
 int graus2 = map(leitura2, 1017,344,0,100);
 
 int graus3 = map(leitura3, 1017,344,0,100);
  
 int graus4 = map(leitura4, 1017,344,0,100);


#### Para calculo do PID é necessario ter a diferença entre os valores dos LDRS, do erro atual, do erro anterior, do tempo atual e o tempo anterior. Com esse dados é possível realizar os calculos do PID: P=Kp x E(t), I=I + Ki x E(t) x Dt, D=(Derro/Dt) x Kd, tendo como calculo final para o servo motor: OUTPUT=P+I+D.

#### Na primeira metade do código de controle automático, ocorre o controle do primeiro par de LDRs. Nessa linha do código a variável input1 recebe a diferença de brilho entre os LDRs.

 int input1 = graus1-graus2;//"P" e "I" e "D"
 
#### Nessa parte do codigo a variável (erro1_ant) recebe o valor que está armazenado na variável (erro1), com o erro já armazenado na variável (erro1_ant), a variável (erro1) ficará livre para receber o novo valor do erro atual do sistema.

 erro1_ant= erro1;//calculo do "I" e "D"
 
 erro1 = 0-input1;//calculo do "P" e "I" e "D"
 
#### Nessa linha do codigo a variável (derro1) recebe o erro atual subtraido do erro anterior para o calculo da derivada.

 derro1 = erro1-erro1_ant;// calculo do "D"
 
#### Nessa parte do codigo a variável (t_ant1) recebe o valor que está armazenado na variável (t_atual1), com o tempo já armazenado na variável (t_ant1), a variável (t_atual1) ficará livre para receber o novo valor do tempo atual do sistema em milissegundos.

 t_ant1 = t_atual1;//"I" e "D"
 
 t_atual1 = millis();//"I" e "D"
 
#### Nessa linha do codigo a variável (dt1) recebe o tempo atual subtraido do tempo anterior para o calculo da integral.
 
 int dt1 = t_atual1-t_ant1;//"I" e "D"
 
#### Nessa parte do codigo é calculado a integral que vai ser usada no PID, fazendo o valor de integral variar entre 5 e -5. Quando o valor fica positivo faz o servo ir pra um sentido e quando negativo faz o servo ir sentido contrário.
 
 integral1 = integral1+0.0001*erro1*dt1;
 
 if (integral1>5){
 
  integral1=5;
  
 }
 
 if (integral1<-5){
 
  integral1=-5;
  
 }

#### Nessa parte do codigo é calculado a derivada que nada mais é do que: (erro atual - erro anterior)/(tempo atual - tempo anterior), e multiplicado pela constante Kd = 200.

 derivada1 = (derro1/dt1)*200;
 
#### Nessa parte do codigo é calculado o valor do PID que vai para o servo variando este de 0 a 60 de acordo com os angulos definidos  pela equipe para melhor aproveitamento dos movimentos do servo.

    pos1 = pos1+(float)(erro1*0.05)+(float)(integral1)+(derivada1);
    
  if (pos1>60){
  
    pos1 = 60;
    
}

  if (pos1<0){
  
    pos1 = 0;
      
}

meuservo1.write(pos1);

#### Essa parte do codigo é utilizada para controlar os movimentos do segundo par de LDRS. Nessa linha, a variável input2 recebe a diferença de luminosidade entre o segundo par de LDRs.

int input2 = graus3-graus4;//"P" e "I" e "D"

#### Nessa parte do codigo a variável (erro2_ant) recebe o valor que está armazenado na variável (erro2), com o erro já armazenado na variável (erro2_ant), a variável (erro2) ficará livre para receber o novo valor do erro atual do sistema.

erro2_ant= erro2;//"I" e "D"

erro2 = 0-input2;//"P" e "I" e "D"

#### Nessa linha do codigo a variável (derro2) recebe o erro atual subtraido do erro anterior para o calculo da derivada.

derro2 = erro2-erro2_ant;//"D"

#### Nessa parte do codigo a variável (t_ant2) recebe o valor que está armazenado na variável (t_atual2), com o tempo já armazenado na variável (t_ant2), a variável (t_atual2) ficará livre para receber o novo valor do tempo atual do sistema em milissegundos.

t_ant2 = t_atual2;//"I" e "D"

 t_atual2 = millis();//"I" e "D"
 
#### Nessa linha do codigo a variável (dt2) recebe o tempo atual subtraido do tempo anterior para o calculo da integral.
 
 int dt2 = t_atual2-t_ant2;//"I" e "D"
 
#### Nessa parte do codigo é calculado a integral que vai ser usada no PID, fazendo o valor da integral variar entre 5 e -5. Quando o valor fica positivo faz o servo ir pra um sentido e quando negativo faz o servo ir sentido contrário.
 
 integral2 = integral2+0.0001*erro2*dt2;
 
 if (integral2>5){
 
  integral2=5;
  
 }
 
 if (integral2<-5){
 
  integral2=-5;
  
 }
 
#### Nessa parte do codigo é calculado a derivada que nada mais é do que: (erro atual - erro anterior)/(tempo atual - tempo anterior), e multiplicado pela constante Kd = 200.
 
 derivada2 = (derro2/dt2)*200;
 
  pos2 = pos2+(float)(erro2*0.05)+(float)(integral2)+(derivada2);
  
if (pos2>60){

  pos2 = 60;
  
}

  if (pos2<0){
  
    pos2 = 0;
      
}
meuservo2.write(pos2);

  }
  
  delay(100);
  
}

## CONCLUSÃO
A principal aplicação deste projeto é em painéis fotovoltaicos de usinas de energia solar. Este sistema possibilita um aproveitamento muito maior na conversão de energia fotovoltaica uma vez que os painéis solares estariam sempre voltados em direção ao sol.
Para que essa implementação ocorra, presaremos pesquisar por componentes mais resistentes a intempéries já que os mesmos ficariam expostos no campo e fabricar o produto em escala industrial.
Na aplicação do PID ficou claro a utilidade de de cada um, sendo o P um valor mais atual possivel para o movimento, o I uma integral que varia entre 5 e -5 fazendo o servo não ter movimentos bruscos com pequenas mudanças de luminosidade e o D como se fosse um amortecedor do movimento.


