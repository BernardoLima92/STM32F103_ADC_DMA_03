# STM32F103_ADC_DMA_03
Using ADC trigged by TIM4 Capture Compare 4 Event and DMA (PWM Mode)

Este Exemplo é muito parecido com o exemplo descrito no repositório STM32F103_ADC_DMA_02, que pode ser encontrado neste link:
https://github.com/BernardoLima92/STM32F103_ADC_DMA_02

A principal diferença é que aqui o Canal 4 do Timer 4 é configurado como "PWM Generation No Output", enquanto que no exemplo
anterior o Canal 4 do Timer 4 é Configurado como "Output Compare no Output" com o campo MODE configurado como Toggle on Match.

A principal diferença pratica está mostrada na figura abaixo:

Dado o fato que o ADC só é "triggado" nas bordas de subida, quando se usa o modo Output Compare com Toggle on Match os disparos do ADC
só ocorrem a cada dois ciclos do timer, pois é nesses ciclos que ocorre uma borda de subida no OC4REF. A figura abaixo mostra o diagrama 
no tempo do timer configurado como Outptu Compare no modo Toggle on Match:

![triggertime](https://user-images.githubusercontent.com/114233216/192389512-a81ba69e-3ee8-4c53-9223-a3138e88d995.png)


Quando se usa o modo PWM Generation no Output, o disparo do ADC ocorre  em todos os ciclos do timer, pois sempre haverá uma borda de subida
no OC4REF. A figura abaixo mostra o diagrama no tempo do timer configurado como PWM Generation no Output:

![EX6_triggertime](https://user-images.githubusercontent.com/114233216/192388701-0971719b-34fe-4726-94c4-887a772b0057.png)

A sequeência de figuras abaixo ilustra as configurações realizadas no STM32CubeIDE:

Configuração do Clock:
![EX6_Clock](https://user-images.githubusercontent.com/114233216/192389873-81ec5d3c-07b9-48c8-b981-9df7b1a9b5c6.png)


Configuração do TIMER 4:
![EX6_TIM4a](https://user-images.githubusercontent.com/114233216/192389891-f6b71582-d68d-43fa-ad58-073196a53dcf.png)
![EX6_TIM4b](https://user-images.githubusercontent.com/114233216/192389901-ca1be44c-e299-4786-af59-0e23df964348.png)


Configuração do ADC:
![EX6_ADC](https://user-images.githubusercontent.com/114233216/192389970-148d797a-7065-4378-9c4f-3b96d8f2a598.png)


Configuração do DMA:
![DMA_adc](https://user-images.githubusercontent.com/114233216/192389994-d637419f-8338-4f70-9aae-150048b6ff65.png)


