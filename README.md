# Nmap Scan Comparison

Comparative analysis of different Nmap scanning techniques focusing on execution time and information depth.

## Objective 

The objective of this project is to compare different Nmap scanning techniques and analyze the trade-off between execution time and depth of information gathered.
This experiment focuses on understanding how different scan strategies impact visibility, performance, and data exposure during reconnaissance.

### 🇧🇷 Português

O objetivo deste projeto é comparar diferentes técnicas de varredura no Nmap e analisar o equilíbrio entre tempo de execução e profundidade das informações coletadas.
O experimento busca entender como diferentes estratégias de scan impactam a visibilidade, desempenho e exposição de serviços durante a fase de reconhecimento.

### Target

``` bash
scanme.nmap.org (Official Nmap Testing Host)
```

## Methodology

Three different scanning approaches were performed against the same target in order to compare efficiency and information depth.

### 🇧🇷 Português

Foram realizadas três abordagens de varredura diferentes contra o mesmo alvo para comparar eficiência e profundidade das informações obtidas.

## Default Scan

``` bash
nmap scanme.nmap.org
```

![Default Scan Result](https://github.com/user-attachments/assets/6c33fc85-979a-4a38-be38-1f8792a625cc)


The default Nmap scan performs a TCP SYN scan against the 1000 most common ports.
This scan is optimized for speed and is typically used during initial reconnaissance phases to quickly identify open services.


Focus:

-  Fast execution

-  Identification of open ports

-  Basic service recognition

### 🇧🇷 Português

O scan padrão do Nmap realiza uma varredura TCP SYN nas 1000 portas mais comuns.
É otimizado para velocidade e geralmente utilizado na fase inicial de reconhecimento para identificar rapidamente serviços expostos.


Foco:


-  Execução rápida

-  Identificação de portas abertas

-  Reconhecimento básico de serviços

## Full Port Scan

``` bash
nmap -p- scanme.nmap.org
```

![Full Port Scan Result](https://github.com/user-attachments/assets/97866efb-e17d-461d-8230-bd2fcb0c8c3a)


The -p- parameter instructs Nmap to scan the entire TCP port range (1–65535), instead of only the 1.000 most common ports defined in the default configuration.

By default, Nmap scans a limited set of frequently used ports to optimize speed and efficiency. However, services may run on non-standard or uncommon ports, which would not be detected in a default scan.

The full port scan increases visibility by ensuring that no TCP port is left unchecked. This technique is particularly useful during comprehensive reconnaissance phases, where identifying hidden or non-standard services is critical.

However, scanning all ports significantly increases scan duration and may generate higher network noise, increasing the likelihood of detection in monitored environments.

Important Observation:

Since the scan was executed without administrative privileges, Nmap performed a TCP Connect Scan (-sT) instead of a SYN Scan (-sS).

This means full TCP handshakes were completed during the scanning process, making the scan more detectable compared to a half-open SYN scan.

### 🇧🇷 Português

O parâmetro -p- instrui o Nmap a verificar toda a faixa de portas TCP (1–65535), em vez de apenas as 1.000 portas mais comuns definidas na configuração padrão.

Por padrão, o Nmap realiza uma varredura otimizada focada nas portas mais utilizadas, visando maior rapidez. Entretanto, alguns serviços podem estar configurados em portas não convencionais, o que não seria identificado em um scan padrão.

A varredura completa amplia a visibilidade ao garantir que nenhuma porta TCP deixe de ser analisada. Essa abordagem é especialmente útil em fases de reconhecimento mais aprofundadas, nas quais a identificação de serviços ocultos ou fora do padrão pode ser decisiva.

Contudo, o escaneamento de todas as portas aumenta significativamente o tempo de execução e o volume de tráfego gerado, elevando as chances de detecção por sistemas de monitoramento.

Observação Importante:

Como o scan foi executado sem privilégios administrativos, o Nmap utilizou o TCP Connect Scan (-sT) em vez do SYN Scan (-sS).

Isso significa que o handshake TCP foi completado, tornando a varredura mais detectável quando comparada ao modelo half-open.

## Agressive Scan

``` bash
nmap -A scanme.nmap.org
```

![Agressive Scan Result](https://github.com/user-attachments/assets/e8add7c9-cc73-4914-8529-1ea635228b2d)



The -A flag enables multiple advanced enumeration techniques:


-  Service version detection (-sV)

-  Operating system detection (-O)

-  Execution of default NSE scripts

-  Traceroute to the target


Unlike a simple port scan, aggressive mode provides deeper insight into exposed services, underlying technologies, and system characteristics.

However, due to the higher traffic volume and active probing techniques, aggressive scans significantly increase the likelihood of detection by monitoring systems such as IDS/IPS.

### 🇧🇷 Português

O parâmetro -A ativa múltiplas técnicas avançadas de enumeração:


-  Detecção de versão dos serviços (-sV)

-  Identificação do sistema operacional (-O)

-  Execução de scripts padrão do NSE

-  Traceroute até o alvo


Diferente de um simples port scan, o modo agressivo fornece informações mais detalhadas sobre os serviços expostos, possíveis tecnologias utilizadas e características do sistema remoto.

No entanto, devido ao maior volume de tráfego e às técnicas de sondagem ativa, as varreduras agressivas aumentam significativamente a probabilidade de detecção por sistemas de monitoramento como IDS/IPS.

## Results

The scans revealed differences in information depth, execution time, and level of detail collected from the target.

The Default Scan identified the most common open ports and basic service information, providing a quick overview of exposed services.

The Full Port Scan expanded visibility by analyzing all 65,535 TCP ports, confirming whether additional non-standard services were exposed beyond the default range.

The Aggressive Scan provided the most detailed output. In addition to open ports, it identified service versions, operating system fingerprints, and executed default NSE scripts, offering deeper insights into the target environment.

Execution time increased progressively from the Default Scan to the Full Port Scan and reached its highest duration in the Aggressive Scan due to additional probing techniques.

These observations demonstrate how scan configuration directly influences reconnaissance depth and operational footprint.

### 🇧🇷 Português

As varreduras evidenciaram diferenças no nível de detalhamento das informações coletadas, tempo de execução e profundidade da análise.

O Default Scan identificou as portas abertas mais comuns e informações básicas sobre os serviços, fornecendo uma visão inicial do ambiente exposto.

O Full Port Scan ampliou a visibilidade ao analisar todas as 65.535 portas TCP, permitindo confirmar se havia serviços não convencionais além do range padrão.

O Aggressive Scan apresentou o resultado mais detalhado. Além das portas abertas, identificou versões dos serviços, possíveis sistemas operacionais e executou scripts padrão do NSE, oferecendo uma visão mais aprofundada do ambiente alvo.

O tempo de execução aumentou progressivamente do Default Scan para o Full Port Scan, sendo mais elevado no Aggressive Scan devido às técnicas adicionais de sondagem.

Esses resultados demonstram como a configuração da varredura impacta diretamente a profundidade do reconhecimento e o volume de tráfego gerado.

## Comparative Analysis

The comparison below highlights the impact of scan configuration on execution time and reconnaissance depth.
| Scan Type       | Execution Time (seconds) | Depth of Information | Network Noise | Detection Risk |
| --------------- | ------------------------ | -------------------- | ------------- | -------------- |
| Default Scan    | 5.84 s                   | Basic                | Low           | Low            |
| Full Port Scan  | 1206.24 s                | Moderate (All Ports) | Medium        | Medium         |
| Aggressive Scan | 19.69 s                  | High                 | High          | High           |

The Default Scan proved to be the fastest, providing rapid identification of commonly exposed services.

The Full Port Scan dramatically increased execution time due to scanning all 65,535 TCP ports, even when most were closed.

The Aggressive Scan required more time than the default scan but remained significantly faster than the full port scan, while delivering the richest technical details through service version detection, OS fingerprinting, and NSE scripts.

This comparison demonstrates the practical trade-offs between speed, visibility, and operational footprint.

### 🇧🇷 Português

A comparação abaixo evidencia o impacto da configuração da varredura no tempo de execução e na profundidade do reconhecimento.
| Tipo de Scan    | Tempo de Execução (segundos) | Profundidade da Informação | Ruído na Rede | Risco de Detecção |
| --------------- | ---------------------------- | -------------------------- | ------------- | ----------------- |
| Default Scan    | 5.84 s                       | Básica                     | Baixo         | Baixo             |
| Full Port Scan  | 1206.24 s                    | Moderada (Todas Portas)    | Médio         | Médio             |
| Aggressive Scan | 19.69 s                      | Alta                       | Alto          | Alto              |

O Default Scan foi o mais rápido, fornecendo uma identificação rápida dos serviços mais comuns expostos.

O Full Port Scan aumentou drasticamente o tempo de execução ao analisar todas as 65.535 portas TCP, mesmo que a maioria estivesse fechada.

O Aggressive Scan levou mais tempo que o scan padrão, porém permaneceu muito mais rápido que o Full Port Scan, ao mesmo tempo em que entregou o maior nível de detalhamento técnico.

Essa comparação demonstra claramente o equilíbrio entre velocidade, profundidade e impacto operacional.

## Conclusion

This project demonstrated how different Nmap scan configurations directly affect execution time, information depth, and operational footprint.

While the Default Scan provides a fast overview of exposed services, the Full Port Scan expands visibility by analyzing all TCP ports, significantly increasing execution time. The Aggressive Scan delivers the most detailed intelligence by combining multiple enumeration techniques.

Choosing the appropriate scan type depends on the objective of the assessment, balancing speed, stealth, and depth of reconnaissance.

### 🇧🇷 Português

Este projeto demonstrou como diferentes configurações de varredura no Nmap impactam diretamente o tempo de execução, a profundidade das informações coletadas e o impacto operacional.

Enquanto o Default Scan oferece uma visão rápida dos serviços expostos, o Full Port Scan amplia a visibilidade ao analisar todas as portas TCP, aumentando significativamente o tempo de execução. Já o Aggressive Scan fornece o maior nível de detalhamento ao combinar múltiplas técnicas de enumeração.

A escolha do tipo de varredura deve considerar o objetivo da análise, equilibrando velocidade, discrição e profundidade do reconhecimento.
