# Avaliação Experimental dos Protocolos TCP e UDP em Cenários de Streaming de Vídeo

Link google DOCS - https://docs.google.com/document/d/1G4mcdDEMXafLMGLlDLABLj37_yIbvkTvoWYhdTpmucY/edit?usp=sharing

## Introdução

A comunicação em redes de computadores evoluiu significativamente nas últimas décadas, impulsionada pela crescente necessidade de transmitir grandes volumes de dados com baixa latência e alta confiabilidade. Nesse contexto, os protocolos de transporte **TCP (Transmission Control Protocol)** e **UDP (User Datagram Protocol)** desempenham papel fundamental ao definir como os dados são segmentados, transmitidos e reconstruídos entre dispositivos conectados em rede.

Aplicações modernas, como streaming de vídeo ao vivo, jogos online e sistemas de tempo real, exigem diferentes características de comunicação. Dessa forma, a escolha do protocolo de transporte influencia diretamente a experiência do usuário e a eficiência do sistema. Compreender as diferenças práticas entre TCP e UDP torna-se essencial para o desenvolvimento de aplicações que dependem de desempenho e qualidade de serviço.

Embora o UDP seja amplamente utilizado em aplicações sensíveis à latência, existem poucas avaliações experimentais que comparem sistematicamente seu desempenho ao do TCP em ambientes controlados com degradação proposital da rede. Essa análise é particularmente relevante em cenários de streaming ao vivo, nos quais atrasos causados por retransmissões do TCP podem impactar mais negativamente a experiência do usuário do que a perda ocasional de pacotes observada no UDP.

## Objetivo

Este projeto tem como objetivo realizar uma avaliação experimental comparativa entre os protocolos TCP e UDP em um cenário que simula a transmissão contínua de vídeo ao vivo.

Para isso, será desenvolvido um sistema composto por um servidor transmissor e um cliente receptor, responsáveis pelo envio e recebimento de pacotes que representam frames de vídeo. O desempenho dos protocolos será analisado por meio das seguintes métricas:

* Latência média;
* Jitter (variação do atraso);
* Taxa de entrega de pacotes.

Os experimentos serão executados sob três condições distintas de rede:

* **Boa:** baixa latência e ausência de perdas significativas;
* **Média:** latência moderada e pequenas perdas de pacotes;
* **Ruim:** alta latência, jitter elevado e maior taxa de perda de pacotes.

Essa abordagem permitirá avaliar o comportamento de cada protocolo em diferentes cenários e reproduzir os resultados de forma consistente.

## Tecnologias Utilizadas

O projeto será desenvolvido utilizando as seguintes tecnologias:

* **Python** para implementação do servidor e cliente;
* **Socket API** para comunicação direta na camada de transporte;
* **Docker** para isolamento e gerenciamento do ambiente experimental;
* **TC/NETEM** para simulação de condições adversas de rede;
* **Pandas** para processamento dos dados coletados;
* **Matplotlib** para geração de gráficos e visualização dos resultados.

## Metodologia

A comunicação entre servidor e cliente será implementada diretamente sobre sockets TCP e UDP, sem a utilização de camadas intermediárias de aplicação, permitindo observar exclusivamente o comportamento dos protocolos de transporte.

Os componentes serão executados em containers Docker independentes, simulando ambientes distintos de transmissão e recepção. As condições de rede serão controladas por meio da ferramenta **TC/NETEM**, responsável por introduzir parâmetros como:

* Latência;
* Jitter;
* Perda de pacotes.

Durante cada experimento, as métricas de desempenho serão registradas, processadas e posteriormente analisadas por meio de gráficos e relatórios comparativos.

## Resultados Esperados

Espera-se demonstrar, de forma prática e quantitativa, as principais diferenças entre TCP e UDP em aplicações de streaming em tempo real.

Os resultados deverão evidenciar que:

* O TCP oferece maior confiabilidade na entrega dos dados;
* O UDP apresenta menor latência e menor impacto causado por retransmissões;
* O desempenho relativo de cada protocolo varia conforme a qualidade da rede e os requisitos da aplicação.

A partir dessas observações, será possível identificar os cenários em que cada protocolo apresenta vantagens, contribuindo para uma compreensão mais aprofundada de seu uso em aplicações de comunicação em tempo real.
