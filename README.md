# MarS — Caixinha do Tchauzinho 👋

A MarS é uma caixinha robótica que usa um **Arduino Uno**, um sensor ultrassônico HC-SR04 e dois servos para detectar a aproximação de alguém e responder com um tchauzinho.

## Documentação e simulação

- [Documentação do projeto e simulador interativo](documentacao.html)
- [Site publicado](https://jorgehenriqueb.github.io/MarS-Caixinha_Inutil/)

## Funcionamento documentado

1. O HC-SR04 mede a distância até um objeto à frente da caixinha.
2. Uma leitura válida de 1 a 15 cm ativa o sistema uma vez: o servo da base vai a 90° e o servo do braço executa a sequência do tchauzinho.
3. A sequência levanta o braço de 0° a 90°, faz duas oscilações entre 90° e 0° e abaixa o braço.
4. Entre 16 e 24 cm, o sistema mantém o estado atual.
5. A partir de 25 cm, a detecção é liberada e a base retorna a 0°, ficando pronto para uma nova aproximação.
6. Uma leitura 0 representa timeout/ausência de eco válido e não ativa nem rearma o sistema.

O gesto usa movimentos bloqueantes com `delay()`: durante a sequência, o Arduino não faz uma nova leitura do sensor. A simulação na documentação reproduz esse comportamento e anima os ângulos dos servos.

## Componentes e conexões conforme o código fornecido

| Componente | Arduino Uno | Função |
|---|---:|---|
| HC-SR04 TRIG | D7 | Disparo da medição |
| HC-SR04 ECHO | D8 | Retorno do pulso |
| Servo da base | D2 | 0° em repouso e 90° quando detecta alguém |
| Servo do braço | D3 | Movimento do tchauzinho, entre 0° e 90° |

A alimentação dos servos deve ser dimensionada para sua corrente de pico. Não presuma que o pino de 5 V do Arduino Uno possa alimentar os dois servos; se usar fonte externa, una o GND da fonte ao GND do Uno. Confirme a tensão admissível do pino ECHO e todos os ângulos com o hardware real.

## Arquivos

O site é composto por páginas HTML estáticas. O arquivo `documentacao.html` contém a documentação atualizada e a simulação interativa. A página da equipe e a seção de planejamento 5W2H não fazem parte desta atualização.

## Abrir localmente

Abra `index.html` ou `documentacao.html` no navegador. A página usa recursos de estilo via CDN e precisa de conexão com a internet para carregá-los.

## Licença

Nenhuma licença foi especificada neste repositório. Consulte a equipe antes de reutilizar conteúdo ou arquivos do projeto.
