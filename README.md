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





## IMPLEMENTAÇÃO

- O LDR funciona da seguinte maneira, quanto maior a luminosidade incidente no LDR, mais o servo motor se moverá na direção do LDR. Essa movimentação ocorrerá até que todos os LDRs estejam com o mesmo percentual de iluminação.

- O potenciometro é um componente elétrico que possui uma resistência ajustável. Seu valor resistivo foi atrelado a uma variável que representa quantos graus o servo motor irá girar, ou seja, a medida que giramos o potenciometro, sua resistencia aumenta, fazendo com que a variável atrelada a ele sofra mudanças em seus valores e faça o servo motor rotacionar.

- O servo motor é o atuador, é essa peça que recebe os sinais e executa os comandos.

- A Finalidade dos resistores é apenas limitar as correntes que atuam no circuito.

- A protoboard assim como os cabos, são os componentes utilizados para fazer a montagem e interligação de todos os outros componentes do projeto.

- A Finalidade do botão neste projeto é apenas selecionar o tipo de controle que iremos utilizar no painel solar, se é manual (potenciometros), ou automático (LDRs).

- O arduino Uno é a plataforma utilizada para o desenvolvimento do projeto, ele é responsável pela prototipagem, implementação e emulação dos controle de sistemas interativos.

- O LED é um diodo emissor de luz, da sigla em inglês LED. SUa função neste projeto é indicar caso o controle automatico tenha sido ativado.
