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

- **Título do trabalho**: C Wings
- **Parágrafo curto descrevendo o que será implementado**: Simulador de voo arcade inspirado visualmente em Microsoft Flight Simulator 2000 e Pilotwings 64. O jogador pilota um avião sobre uma ilha texturizada com arvores, pista de pouso e outros objetos. O jogo nao possui missoes ou objetivos, mas contara com diferentes tipos de aeronaves, viewports e condicoes de voo.

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

[Clique Aqui](https://www.youtube.com/watch?v=QB_HZeH3X3c)

### Vídeo - Timestamp

> [!IMPORTANT]
> - Coloque aqui um **intervalo de ~30 segundos** do vídeo acima, que
>   será a base de comparação para avaliar se o seu trabalho final
>   conseguiu ou não reproduzir a referência.

- **Timestamp inicial**: 11:00
- **Timestamp final**: 11:30

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

- **Descrição**: Aviao visto em terceira pessoa, sobrevoando uma cidade. Abaixo, pode-se tambem observar um conjunto de meshes para prédios e um rio.

<img width="1707" height="865" alt="image" src="https://github.com/user-attachments/assets/d697be16-256b-4d8a-9c09-a4156677e126" />


#### Imagem 2

- **Descrição**: Visao de primeira-pessoa da cabine. Diferentemente dessa versao do simulador, nos implementaremos uma cabine tri-dimensional com "free-look".

<img width="1727" height="971" alt="image" src="https://github.com/user-attachments/assets/30dfb337-8375-4ae2-bb58-1f709d82bf3e" />


#### Imagem 3

- **Descrição**: Frame exibido no menu principal. Percebe-se neblina mais acentuada e uma nova textura para o ceu, em função de condição climática diferente.

<img width="753" height="436" alt="image" src="https://github.com/user-attachments/assets/0c0421c1-2231-4e02-9338-ea3e25a173d7" />


## Especificação textual

Para cada um dos requisitos abaixo (detalhados no [Enunciado do Trabalho final - Moodle](https://moodle.ufrgs.br/mod/assign/view.php?id=6302370)), escreva um parágrafo **curto** explicando como este requisito será atendido, apontando itens específicos do vídeo/imagens que você incluiu acima que atendem estes requisitos.

### Malhas poligonais complexas

- Modelos de aeronave,
- Arvores do terreno,
- Hangar, 
- O terreno da ilha será uma triangle mesh gerada a partir de um heightmap.

### Transformações geométricas controladas pelo usuário

- O jogador controla a orientação do avião e a potência do motor pelo teclado, o que define a Model matrix do avião a cada quadro.
- A hélice girara com velocidade proporcional à potência do motor, e as superfícies de controle (ailerons e leme) giram conforme os comandos do jogador.

### Diferentes tipos de câmeras

- Terceira pessoa: segue o avião por trás, olhando para ele, como na imagem 1 e 3. O mouse permite orbitar a câmera ao redor do avião.
- Primeira pessoa: posicionada no assento do piloto, como na imagem 2, acompanhando a orientação do avião. O mouse permite olhar ao redor dentro da cabine.

O jogador alterna entre as câmeras com a tecla V.

### Instâncias de objetos

As árvores e predios da ilha serão desenhados várias vezes a partir de um mesmo conjunto de vértices, cada instância com sua própria Model matrix.

### Testes de intersecção

As colisoes do aviao serao testadas com uma multitude de objetos, produzindo diferentes efeitos visuais, como por exemplo:
Aviao x obstaculo, alta velociade: explosao e fim de jogo.
Aviao x obstaculo, baixa velociade: "bounce" para o aviao, som de colisao
Rodas do Aviao x pista, baixa velocidade: pouso bem sucedido.

### Modelos de Iluminação em todos os objetos

Uma luz direcional (sol)
- Lambert: terreno, pista e árvores
- Phong: no avião e água
- Interpolação de Phong no avião, terreno e água

### Mapeamento de texturas em todos os objetos

- Todos os objetos terão cores definidas por imagens com coordenadas UV
- O terreno utilizara texturas "tiled" para diferentes materiais como grama, areia e agua para evitar texturas esticadas.

### Movimentação com curva Bézier cúbica

- Um dirigível sobrevoa a ilha continuamente ao longo de um percurso fechado formado por segmentos de curva de Bézier cúbica, com continuidade de tangente entre os segmentos.
- O jogador podera colidir com o dirigível, causando uma explosao.

### Animações baseadas no tempo ($\Delta t$)

Todas as movimentações usam o tempo decorrido entre quadros: 
- Flight model para o aviao
- Rotação da hélice
- Avanço do parâmetro da curva de Bézier do dirigível

### Funcionalidade extra obrigatória

> [!IMPORTANT]
> - Descreva a funcionalidade extra relacionada à Computação Gráfica
>   que será implementada.
> - Esta funcionalidade também deverá ser documentada no arquivo
>   `README.md` da entrega final.

- Sombras globais projetadas: 
  - O aviao e outros objetos projetarao sombras suas no chao, o que ajudara o jogador a determinar sua altitude durante o pouso e decolagem.
- Neblina:
  - Para evitramos distorcoes como Z-fighting, renderizaremos a cena com neblina que crescera exponencialmente com a distancia da camera.

## Limitações esperadas

> [!IMPORTANT]
> - Coloque aqui uma lista de detalhes visuais ou de interação que
>   aparecem no vídeo e/ou imagens acima, mas que você **não pretende
>   implementar** ou que você **irá implementar parcialmente**.
> - Para cada item, **explique por que** não será implementado ou por
>   que será implementado parcialmente.

- Unico mapa: O jogo tera apenas uma ilha. 
- Modelo de voo simplificado: A fisica do aviao sera propositalmente arcade, para podermos focar mais em shading
- HUD e menus simplificados: implementaremos a menor quantidade de HUD possivel. Provavelmente apenas um "main menu" e indicadores de velocidade e altitude.
- Agua simplificada: A agua potencialmente nao sera animada. Sendo apenas uma textura tiled e reflexiva.
