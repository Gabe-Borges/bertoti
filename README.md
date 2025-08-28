## Meus comentários sobre o primeiro trecho do livro Software Engineering at Google:

  O texto explica que programação e engenharia de software não são exatamente a mesma coisa. Programação está mais ligada a escrever código, enquanto engenharia de software envolve aplicar conhecimentos teóricos e métodos estruturados para criar sistemas mais precisos e confiáveis, de forma semelhante ao trabalho de engenheiros de outras áreas.

Em profissões como engenharia civil ou mecânica, há normas e práticas muito rigorosas para evitar erros graves. Na programação, historicamente, essas regras não eram tão seguidas, mas, com a presença crescente do software no cotidiano, torna-se necessário adotar métodos mais rigorosos. O Google, com sua experiência, busca apresentar formas de tornar o desenvolvimento de software mais confiável.



## Meu comentário sobre o segundo trecho:

  Esse segundo trecho apresenta a ideia de que engenharia de software não é apenas escrever código, mas também incluir todas as ferramentas e processos que ajudam a criar e manter esse código ao longo do tempo. A questão central é como manter o código útil e sustentável durante toda a sua vida, desde a criação até a desativação.

A visão do Google, baseada em sua experiência, é que engenharia de software pode ser vista como “programação integrada ao longo do tempo”, ou seja, levando em conta as mudanças e a manutenção contínua. O livro destaca três princípios fundamentais que devem guiar a forma como o código é projetado e escrito:

1. Tempo e Mudança – como o código precisa se adaptar durante sua vida útil;

2. Escala e Crescimento – como a organização deve se ajustar à medida que evolui;

3. Compensações e Custos – como tomar decisões considerando as lições dos dois pontos anteriores.



## Exemplos de tradeoffs:

**1. Desempenho vs. Legibilidade do Código:**

Exemplo: Ao otimizar um trecho de código para melhorar o desempenho (por exemplo, usando técnicas como cache ou algoritmos mais complexos), o código pode se tornar mais difícil de ler e manter.

Tradeoff: Em um projeto de software, há uma escolha entre otimizar o código para ser mais rápido e eficiente ou mantê-lo simples e fácil de entender para os desenvolvedores, facilitando a manutenção e a evolução do sistema.

**2. Escalabilidade vs. Complexidade Arquitetural:**

Exemplo: Ao projetar um sistema que precisa lidar com um grande volume de tráfego, você pode optar por uma arquitetura distribuída que permita escalabilidade horizontal (como microserviços). No entanto, essa abordagem tende a aumentar a complexidade do sistema, pois requer gestão de vários serviços, comunicação entre eles e controle de falhas.

Tradeoff: A busca por escalabilidade pode resultar em um sistema mais complexo, que exige mais esforço para desenvolvimento, monitoramento e manutenção.

**3. Desenvolvimento Rápido vs. Qualidade do Código:**

Exemplo: Em um cenário de desenvolvimento ágil, pode-se priorizar a entrega rápida de funcionalidades, o que pode resultar em código com menos cobertura de testes, maior dívida técnica ou maior acoplamento entre componentes.

Tradeoff: Sacrificar a qualidade do código para entregar funcionalidades rapidamente pode acelerar o desenvolvimento inicial, mas a longo prazo pode resultar em um sistema mais difícil de manter e propenso a falhas.

## Diagrama de Classes UML:

<img width="686" height="227" alt="Padaria" src="https://github.com/user-attachments/assets/c2a9bd4b-ff94-4038-900d-ce8b6cf15a62" />




