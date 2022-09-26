# STM32F103_ADC_DMA_03
Using ADC trigged by TIM4 Capture Compare 4 Event and DMA (PWM Mode)

Este Exemplo é muito parecido com o exemplo descrito no repositório STM32F103_ADC_DMA_03, que pode ser encontrado neste link:
https://github.com/BernardoLima92/STM32F103_ADC_DMA_02

A principal diferença é que aqui o Canal 4 do Timer 4 é configurado como "PWM Generation No Output", enquanto que no exemplo
anterior o Canal 4 do Timer 4 é Configurado como "Output Compare no Output" com o campo MODE configurado como Toggle on Match.

A principal diferença pratica está mostrada na figura abaixo:

Dado o fato que o ADC só é "triggado" nas bordas de subida, quando se usa o modo Output Compare com Toggle on Match os disparos do ADC
só ocorrem a cada dois ciclos do timer, pois é nesses ciclos que ocorre uma borda de subida.

![triggertime](https://user-images.githubusercontent.com/114233216/192389512-a81ba69e-3ee8-4c53-9223-a3138e88d995.png)


Quando se usa o modo PWM Generation no Output, o disparo do ADC ocorre  em todos os ciclos do timer, pois sempre haverá uma borda de subida
no TIM4_CCR4.

![EX6_triggertime](https://user-images.githubusercontent.com/114233216/192388701-0971719b-34fe-4726-94c4-887a772b0057.png)
