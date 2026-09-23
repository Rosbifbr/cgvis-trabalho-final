# Especificação da Implementação

> [!CAUTION]
> - Você <ins>**não pode utilizar ferramentas de IA para escrever esta
>   especificação**</ins>

> [!WARNING]
> - Após a entrega da primeira versão completa, esta especificação não
>   poderá ser alterada. A implementação final deverá corresponder ao que
>   estiver descrito neste arquivo.

## Integrantes da dupla

- **Aluno 1 - Nome**: Rodrigo Guimarães Ourique
- **Aluno 1 - Cartão UFRGS**: 581169

- **Aluno 2 - Nome**: Patrick Alves de Queiros
- **Aluno 2 - Cartão UFRGS**: 287729

## Detalhes do que será implementado

- **Título do trabalho**: Lite Souls
- **Parágrafo curto descrevendo o que será implementado**: Jogo de combate corpo-a-corpo em primeira e terceira pessoa, PVE (player versus environment) com mapas predefinidos, IA simples para diferentes tipos de adversarios e mecanica de combate "souls-like", envolvendo tipos diferentes de ataque, bloqueio, e esquivo. 

<!--
## Anotacoes do grupo
Escopo dos assets e mecanica
- O jogo implementara os seguintes assets: 
  - 4 tipos de inimigos, potencialmente governados por IA diferente, com capacidade simples de pathfinding.
  - 4 mapas, cada um introduzindo um novo tipo de inimigo e arma.
  - 4 armas: Garrafa quebrada, Taco de Baseball, Tijolo, Garrucha
- A mecanica do jogo sera a seguinte. Para cada nivel, você deverá:
  - Coletar pontos e colecionaveis (objetos brilhantes)
  - Coletar chaves para abrir portas
  - Matar todos os inimigos para obter pontuacao adicional
  - Chegar na posicao de chegada para ir ao proximo nivel
-->


## Especificação visual

### Vídeo - Link

> [!IMPORTANT]
> - Coloque aqui um link para um vídeo que mostre a aplicação gráfica
>   de referência que você vai implementar. **Sua implementação deverá
>   ser o mais parecido possível com o que é mostrado no vídeo (mais
>   detalhes abaixo).**
> - **Você não pode escolher como referência: (1) algum trabalho realizado
>   por outros alunos desta disciplina, em semestres anteriores. (2) Minecraft.**
> - Por exemplo, você pode colocar um vídeo de um jogo que você gosta,
>   e seu trabalho final será uma re-implementação do jogo.
> - O vídeo pode ser um link para YouTube, Google Drive, ou arquivo mp4 dentro
>   do próprio repositório. Mas, garanta que qualquer um tenha
>   permissão de acesso ao vídeo através deste link.

<mark>`<preencher>`</mark>

### Vídeo - Timestamp

> [!IMPORTANT]
> - Coloque aqui um **intervalo de ~30 segundos** do vídeo acima, que
>   será a base de comparação para avaliar se o seu trabalho final
>   conseguiu ou não reproduzir a referência.

- **Timestamp inicial**: <mark>`<preencher>`</mark>
- **Timestamp final**: <mark>`<preencher>`</mark>

### Imagens

> [!IMPORTANT]
> - Coloque aqui **três imagens** capturadas do vídeo acima, que você
>   irá usar como ilustração para as explicações que vêm abaixo.
> - As imagens devem estar armazenadas neste repositório, no diretório
>   `images/spec/`, com os nomes `image1`, `image2` e `image3`.
> - Cada imagem deve usar o formato `.jpg` ou `.png`. Ajuste a extensão
>   nos vínculos abaixo para que corresponda ao arquivo armazenado.
> - Escolha imagens que correspondam a momentos do intervalo indicado
>   acima ou que sejam relevantes para a comparação com a implementação.

#### Imagem 1

- **Descrição**: <mark>`<preencher>`</mark>

![Imagem 1](images/spec/image1.jpg)

#### Imagem 2

- **Descrição**: <mark>`<preencher>`</mark>

![Imagem 2](images/spec/image2.jpg)

#### Imagem 3

- **Descrição**: <mark>`<preencher>`</mark>

![Imagem 3](images/spec/image3.jpg)

## Especificação textual

Para cada um dos requisitos abaixo (detalhados no [Enunciado do Trabalho final - Moodle](https://moodle.ufrgs.br/mod/assign/view.php?id=6302370)), escreva um parágrafo **curto** explicando como este requisito será atendido, apontando itens específicos do vídeo/imagens que você incluiu acima que atendem estes requisitos.

### Malhas poligonais complexas
Estarao presentes em:
  - Tipos diferentes de armas
  - Modelos dos inimigos/IA
  - Potencialmente objetos no mapa
  - Solo do mapa
### Transformações geométricas controladas pelo usuário
Diretamente: 
  - Movimentação do jogador/camera
  - Animacoes do jogador
  - <Talvez> Interacoes com o cenario
Indiretamente:
  - Inimigos de IA

### Diferentes tipos de câmeras
  - Terceira-Pessoa
  - Primeira-pessoa

### Instâncias de objetos
  - Inimigos do mesmo tipo

### Testes de intersecção
O jogo devera implementar testes de intersecção nas seguintes ocasioes
  - Colisao do jogador com objetos do mapa
  - Intersecção de linha de disparo/mira da garrucha com o mapa ou com um inimigo (hitscan)

### Modelos de Iluminação em todos os objetos
- Iluminação Lambert para superficies difusas
- Iluminacao Phong para superficies especulares, como vidros, agua e metais polidos.

### Mapeamento de texturas em todos os objetos
- As texturas serao todas definidas por imagens
- Usaremos mapeamento UV

### Movimentação com curva Bézier cúbica
- Implementaremos arremesso de projeteis pelo jogador, que se movimentarao utilizando uma curva Bézier.

### Animações baseadas no tempo ($\Delta t$)
- Serao implementadas para a IA, jogador e projeteis arremessados.

### Funcionalidade extra obrigatória

> [!IMPORTANT]
> - Descreva a funcionalidade extra relacionada à Computação Gráfica
>   que será implementada.
> - Esta funcionalidade também deverá ser documentada no arquivo
>   `README.md` da entrega final.

- Pretendemos implementar:
  - Neblina que cresce exponencialmente com a distancia
  - Efeitos de particula simples, como splashes de agua e impactos das armas no ambiente.

## Limitações esperadas

> [!IMPORTANT]
> - Coloque aqui uma lista de detalhes visuais ou de interação que
>   aparecem no vídeo e/ou imagens acima, mas que você **não pretende
>   implementar** ou que você **irá implementar parcialmente**.
> - Para cada item, **explique por que** não será implementado ou por
>   que será implementado parcialmente.

<mark>`<preencher>`</mark>
