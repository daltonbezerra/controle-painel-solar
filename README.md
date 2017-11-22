# Painel Solar Seguidor de Luz

Professor: Afonso Alves

Alunos:
Lucas Valente,
Rodrigo Lopes,
Dalton Bezerra,
Rodrigo Paulo


## INTRODUÇÃO

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


## FLUXOGRAMA

 
![image](https://user-images.githubusercontent.com/32208559/33126381-6bbd47f2-cf6b-11e7-8340-d3f78960ac3e.png)


## DIAGRAMA DE BLOCOS


![whatsapp image 2017-11-21 at 21 28 22](https://user-images.githubusercontent.com/32208559/33126487-d15af262-cf6b-11e7-9938-c9dfa28f55dd.jpeg)


## ESQUEMÁTICO E PLANEJAMENTO

![image](https://user-images.githubusercontent.com/32208559/33126554-14244076-cf6c-11e7-810a-064e7f2e85b9.png)


Esquemático do projeto no tinkerCad


![image](https://user-images.githubusercontent.com/32208559/33126609-43082d08-cf6c-11e7-9629-a4478dba676a.png)


Planejamento


# IMPLEMENTAÇÃO


- O LDR funciona da seguinte maneira, quanto maior a luminosidade incidente no LDR, mais o servo motor se moverá na direção do LDR. Essa movimentação ocorrerá até que todos os LDRs estejam com o mesmo percentual de iluminação.



![image](https://user-images.githubusercontent.com/32208559/33126678-763aaf20-cf6c-11e7-81c9-d140fa7f24d6.png)

Imagem 1: LDR


- O potenciometro é um componente elétrico que possui uma resistência ajustável. Seu valor resistivo foi atrelado a uma variável que representa quantos graus o servo motor irá girar, ou seja, a medida que giramos o potenciometro, sua resistencia aumenta, fazendo com que a variável atrelada a ele sofra mudanças em seus valores e faça o servo motor rotacionar.


![image](https://user-images.githubusercontent.com/32208559/33126721-aad35976-cf6c-11e7-9387-fb871d73f64b.png)

Imagem 2: Potenciômetro


- O servo motor é o atuador, é essa peça que recebe os sinais e executa os comandos.


![image](https://user-images.githubusercontent.com/32208559/33126737-bead136a-cf6c-11e7-9351-65c6e30d1d20.png)

Imagem 3: Servo Motor


- A Finalidade dos resistores é apenas limitar as correntes que atuam no circuito.


![image](https://user-images.githubusercontent.com/32208559/33126751-d217aec4-cf6c-11e7-80cd-b257a3ec822d.png)

Imagem 4: Resistor


- A protoboard assim como os cabos, são os componentes utilizados para fazer a montagem e interligação de todos os outros componentes do projeto.


![image](https://user-images.githubusercontent.com/32208559/33126767-e1f50062-cf6c-11e7-962e-4e1f1b5811d2.png)

Imagem 5: Protoboard


- A Finalidade do botão neste projeto é apenas selecionar o tipo de controle que iremos utilizar no painel solar, se é manual (potenciometros), ou automático (LDRs).


![image](https://user-images.githubusercontent.com/32208559/33126786-f4aa815a-cf6c-11e7-9fdb-70167ade546e.png)

Imagem 6: Botão joystick


- O arduino Uno é a plataforma utilizada para o desenvolvimento do projeto, ele é responsável pela prototipagem, implementação e emulação dos controle de sistemas interativos.


![image](https://user-images.githubusercontent.com/32208559/33126799-084ab392-cf6d-11e7-86f8-86e5754f8154.png)

Imagem 7: Arduino Uno


- O LED é um diodo emissor de luz, da sigla em inglês LED. SUa função neste projeto é indicar caso o controle automatico tenha sido ativado.


![image](https://user-images.githubusercontent.com/32208559/33126819-1c6cfaba-cf6d-11e7-9218-a96aeddf1ee6.png)

Imagem 8: LED
