---
title: Computação Embarcada - IOs (Input/Output)
author: Rafael Corsi - rafael.corsi@insper.edu.br
date: Fevereiro 2018
---


---
pandoc-latex-tip:
  - classes: [warning]
    icons: [{name: warning, color: black}]
  - classes: [read]
    icons: file-text
---

<div class="alert">
 Até o começo da aula do dia 
</div>

# Visão Geral


Quando trabalhamos com computação embarcada, devemos ter um conhecimento mais profundo do alvo do programa (hardware) já que não existe uma camada de abstração de hardware (HAL) tal como em um sistema operacional de alto nível (Linux, Windows, Android, ...).

O correto entendimento do sistema é crucial para o bom funcionamento do programa, pois a aplicação interfaceia diretamente com o mundo externo, manipulando entradas e saídas do sistema (Input e Output = I/O). Esses I/Os podem estar conectados a atuadores, sensores, memórias, interface com o usuário, protocolos de comunicação e muito outros dispositivos que em conjunto formam um sistema embarcado.

[Podemos]{.warning} : classificar esse entendimento em 3 níveis :

1.  Hardware (Placa de circuito Impresso - PCB)
1.  Microcontrolador
1.  Programa (firmware)

O hardware é um conjunto de componentes eletrônicos (microcontrolador inclusive) que forma uma eletrônica embarcada. No hardware estão partes como : fonte de alimentação, memórias externas, conectores, LCD.

O microcontrolador é o dispositivo central do hardware, sendo o responsável pelo controle e supervisão dos demais componentes da placa. O firmware é o código executado pelo microcontrolador que é capaz de manipular e processar sinais do mundo externo. 

<div class="question">
Diagrama de blocos: Esboce um diagrama de blocos que ilustre a interação entre o microcontrolador, hardware e firmware.
</div>

## SAME-70 (microcontrolador Arm)

[(]{.read}*Utilize o manual encontrado em : *Manuais/**SAM-E70-XPLD*** para resolução dessa secção.)*

Com um mercado de 16.5 bilhões de dólares em 2013 [^1] existe uma enorme diversidade de microcontroladores, cada um com uma especificidade. Conhecer o alvo do seu código é um fator primordial para o funcionamento correto do sistema.

<div class="question">
Microcontrolador Identifique a família e e liste as especificidades do microcontrolador utilizado no curso.
</div>

Os microcontroladores ofertados pelo mercado diferenciam-se principalmente pela sua arquitetura (CORE), quantidade de memória interna (RAM, ROM), e pelos periféricos que o compõem.

<div class="question">
Memória Liste os tipos de memórias internas do microcontrolador SAM-E70 e seus tamanhos.
</div>

<div class="question">
Memória II Porque é importante saber quanto de memória um uC possui ?
</div>

## Periféricos

Periféricos são pequenos dispositivos eletrônicos que junto com a unidade de processamento (CORE) e memórias compõem um microcontrolador. Os periféricos são responsáveis por executar tarefas simples simultaneamente ao processamento principal do CORE, muitas vezes, adicionam funcionalidades extras ao sistema, tais como: conversor analógico digital (A/D), protocolo de comunicação I2C, USB, ... . 

A boa utilização dos periféricos torna o código mais robusto e permite a otimização da utilização do processamento do microcontrolador, um mau uso desses periféricos pode tornar o projeto inviável, mesmo com o melhor processador do mercado. Fig. [\[fig:cortexE70\]](#fig:cortexE70){reference-type="ref" reference="fig:cortexE70"} ilustra a arquitetura interna do microcontrolador SAM-E70, e seus periféricos.

![diagrama de blocos sam-e7 *(cortex-m7-sam-e70 - pg. 7)* \label{"fig:cortexe70"}](./figs/cortexE70.pdf){width=85%}

<div class="question">
Periféricos Escolha um dos periféricos do microcontrolador (ADC, DAC, TC, USB, Ethernet, ...) e explique sua funcionalidade.
</div>

<div class="question">
Watchdog O que é watchdog timer e qual é sua utilização ?
</div>

<div class="question">
Custo Pesquise nos fornecedores qual o valor de mercado do chip utilizado no kit de desenvolvimento SAM-E70.
</div>

# SAM-E70-XPLD hardware

[(]{.read}Utilize o documento encontrado em : *Manuais/**Cortex-M7-SAM-E70*** para resolução dessa secção.)

Utilizaremos ao longo do curso um kit de desenvolvimento (hardware) desenvolvida pela Atmel chamada de SAM-E70 XPLD, esse kit possui em seu núcleo o processador ARM Cortex-M7, e algumas outras funcionalidades tais como: memória externa, SD-Card, Ethernet, USB. Essas funcionalidades extras são também chamadas de periféricos, mas agora não sendo referido aos periféricos do uC mas sim aos periféricos da placa.

A Fig. a seguir, extraída do manual do kit de desenvolvimento ilustra como os Demais Periféricos estão conectados no microcontrolador.

<div class="question">
Com os conceitos desenvolvidos até aqui, repense o diagrama da Questão 1.1
</div>


![Periféricos SAM-E70-XPLD\ *(SAM-E70-XPLD - pg. 3)*\label{"fig:E70XPLD"}](./figs/E70XPLD.pdf){width="1\linewidth"} 
