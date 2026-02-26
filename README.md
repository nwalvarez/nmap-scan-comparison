# Nmap Scan Comparison

Comparative analysis of different Nmap scanning techniques focusing on execution time and information depth.

## Objective 

The objective of this project is to compare different Nmap scanning techniques and analyze the trade-off between execution time and depth of information gathered.
This experiment focuses on understanding how different scan strategies impact visibility, performance, and data exposure during reconnaissance.


O objetivo deste projeto é comparar diferentes técnicas de varredura no Nmap e analisar o equilíbrio entre tempo de execução e profundidade das informações coletadas.
O experimento busca entender como diferentes estratégias de scan impactam a visibilidade, desempenho e exposição de serviços durante a fase de reconhecimento.

### Target

``` bash
scanme.nmap.org (Official Nmap Testing Host)
```

## Methodology

Three different scanning approaches were performed against the same target in order to compare efficiency and information depth.


Foram realizadas três abordagens de varredura diferentes contra o mesmo alvo para comparar eficiência e profundidade das informações obtidas.

## Default Scan

``` bash
nmap scanme.nmap.org
```

<img width="822" height="336" alt="image" src="https://github.com/user-attachments/assets/6c33fc85-979a-4a38-be38-1f8792a625cc" />

The default Nmap scan performs a TCP SYN scan against the 1000 most common ports.
This scan is optimized for speed and is typically used during initial reconnaissance phases to quickly identify open services.


Focus:

. Fast execution
. Identification of open ports
. Basic service recognition


O scan padrão do Nmap realiza uma varredura TCP SYN nas 1000 portas mais comuns.
É otimizado para velocidade e geralmente utilizado na fase inicial de reconhecimento para identificar rapidamente serviços expostos.


Foco:


. Execução rápida
. Identificação de portas abertas
. Reconhecimento básico de serviços

## Full Port Scan

``` bash
nmap -p- scanme.nmap.org
```

<img width="819" height="339" alt="image" src="https://github.com/user-attachments/assets/97866efb-e17d-461d-8230-bd2fcb0c8c3a" />

## Agressive Scan

``` bash
nmap -A scanme.nmap.org
```

imagem 3

## Results

## Comparative Analysis

## Conclusion
