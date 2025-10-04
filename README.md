# Gerador da Folha 40×40 — Teste de Atenção Concentrada (BPA)

Este projeto disponibiliza um **gerador de folha de estímulos 40×40** para o Teste de Atenção Concentrada (parte da *Bateria Psicológica para Avaliação da Atenção – BPA*).
O alvo (estímulo correto) é o **retângulo metade-esquerda preta / metade-direita branca (50/50)**, enquadrado por moldura de espessura fixa. A grade é **20×20 células** (cada célula 40 px, com espaçamento entre células), e o **crivo de resposta** segue o padrão por linha: **7, 5, 7, 5, …** alvos (alternando) — o restante são distratores.

> **Por que isso importa?**
> O padrão 7/5 controla a **densidade de alvos** por linha, reduzindo vieses de padrão e mantendo a **carga atencional** estável ao longo da folha, sem “faixas” fáceis ou difíceis demais. É um compromisso entre validade do estímulo e aplicação prática.

---

## Principais características

* **Gerador Web (HTML + SVG)**: abra o arquivo `gerador-folha-40x40-metade-esquerda-v2.html` no navegador, clique em **Regerar** para obter uma nova disposição aleatória e **Baixar SVG** para exportar em alta qualidade.
* **Alvo padronizado (50/50)** com moldura de stroke fixo (não varia ao escalar) e *shape-rendering* configurado para nitidez na impressão.
* **Distratores variados** (barras, diagonais, losango, triplet, quadrantes etc.), definidos como *symbols* SVG para performance e consistência visual.
* **Impressão nítida** (SVG vetorial) e **estilização via CSS** quando embutido em páginas — pensado para a comunidade web que deseja integrar o teste diretamente em sites/aplicações.

---

## Estrutura e parâmetros

* **Grade**: `ROWS = 20`, `COLS = 20`
* **Célula**: `CELL = 40` (px), com espaçamento `GAP = 6`
* **Crivo (alvos por linha)**: `TARGETS_PER_ROW = [7,5,7,5,...]`
* **Alvo**: `#target` (metade esquerda preta, metade direita branca)
* **Distratores**: `bar-right`, `bar-top`, `bar-bottom`, `bar-center`, `diag-fwd`, `diag-back`, `tri-edges`, `top-and-right`, `diamond`, `triplet`, `quad-UL`, `quad-LR`
* **Exportação**: botão “Baixar SVG” salva como `folha-simbolos-40x40-metade-esquerda.svg`.

> Todos os itens acima estão definidos no HTML/SVG do gerador e podem ser ajustados no código caso você queira um outro formato de grade, espaçamento ou conjunto de distratores.

---

## Como usar

1. **Abrir** `gerador-folha-40x40-metade-esquerda-v2.html` no navegador.
2. Clicar em **Regerar** para produzir uma nova variação (randomizada).
3. Clicar em **Baixar SVG** para salvar a folha final e imprimir em A4 ou incorporar onde desejar.
4. **Impressão recomendada**: sem “Ajustar à página”, margens mínimas e qualidade alta (o SVG é vetorial).

Se preferir, utilize diretamente os SVGs incluídos no repositório, como `folha-simbolos-40x40-metade-esquerda-v2.svg`.

---

## CSS / Web (por que “imagens em CSS”?)

Os símbolos foram pensados para **uso web**, com formas vetoriais (SVG) que podem ser **estilizadas via CSS** (por exemplo, controle de stroke, fill e escala sem perda). Isso facilita a vida de quem constrói **sites e aplicações** que precisam gerar, exibir ou imprimir o teste diretamente no navegador — sem depender de imagens rasterizadas.

Exemplo simples de estilização:

```html
<style>
  svg .cell { vector-effect: non-scaling-stroke; }
  svg .cell .frame { stroke: #000; stroke-width: 2; }
</style>
```

> No gerador, as formas estão declaradas como `<symbol>` SVG e reutilizadas via `<use>`, o que reduz peso e mantém a consistência.

---

## Motivação do projeto

* **Acessibilidade e padronização**: compartilhar um gerador aberto e reproduzível, com **crivo 7/5** e alvo 50/50 padronizado, facilita a **reprodução fiel** do material.
* **Integração web**: permitir que equipes de produto, educação e psicometria integrem a folha de estímulos diretamente em **páginas web**, com **download imediato em SVG** para impressão.
* **Comunidade**: reduzir retrabalho na criação manual de folhas; fomentar contribuições (novos distratores, tamanhos, folhas alternativas).

---

## Boas práticas e validação

* **Randomização**: cada clique em “Regerar” cria uma nova distribuição de alvos e distratores **respeitando o crivo 7/5** por linha.
* **Moldura consistente**: *vector-effect: non-scaling-stroke* garante que a espessura da moldura **não distorça** ao escalar.
* **Checagem rápida**: conte os alvos por linha (devem alternar 7/5). Se desejar, adicione um contador automático (ex.: percorrer os `<use>` com `href="#target"`).

---

## Limitações e responsabilidade de uso

Este material **não substitui** instrumentos padronizados, manuais técnicos e a atuação de **profissionais habilitados**. A aplicação, correção e interpretação de testes psicológicos devem seguir a legislação e diretrizes do conselho profissional competente.
Use este gerador como **apoio técnico/visual** para estudos, desenvolvimento de ferramentas e treinamentos.

---

## Roadmap (idéias de evolução)

* Parâmetro de **semente (seed)** para reproduzir uma mesma folha.
* Geração de **PDF** direto no navegador.
* Variações do alvo (ex.: metade direita, inversões, outros contrastes) e **novos distratores**.
* **Temas CSS** (alto contraste / monocromático para impressão econômica).
* Layout pronto para **A4** com marcas de corte e legenda de contagem.

---

## Licença

**Desenvolvido por:** Rogério Moreira Alves Júnior — *abc Ensina*

Este projeto é distribuído sob as seguintes licenças:

* **Código-fonte (HTML/JS/CSS):** Licenciado sob a **MIT License** — uso, modificação e redistribuição livres, inclusive para fins comerciais, desde que mantido o aviso de copyright.
* **Recursos gráficos (SVGs, ícones e variações de estímulos):** Licenciados sob **Creative Commons Attribution 4.0 International (CC BY 4.0)** — reutilização livre com **atribuição obrigatória** ao autor e ao repositório.

> **Atribuição sugerida:**
> “Folha 40×40 e símbolos do Teste de Atenção Concentrada (BPA) por **Rogério Moreira Alves Júnior / abc Ensina** — repositório público (MIT para código / CC BY 4.0 para SVGs).”

**Contribuições:** Ao enviar uma contribuição (issue/PR), o colaborador declara ter direito sobre o material submetido e **aceita a distribuição sob as mesmas licenças** (MIT e CC BY 4.0, conforme aplicável).

---

## Arquivos relevantes

* `gerador-folha-40x40-metade-esquerda-v2.html` — gerador com botões **Regerar** e **Baixar SVG**.
* `folha-simbolos-40x40-metade-esquerda-v2.svg` — exemplo de folha exportada.
* `alvo-metade-esquerda-40x40-v2.svg` — símbolo de alvo isolado.

---

## Propósito colaborativo

O propósito deste repositório é **fortalecer uma rede colaborativa entre desenvolvedores, designers e pesquisadores** interessados em criar e aprimorar recursos gráficos e digitais para testes psicológicos, especialmente o **Teste de Atenção Concentrada (BPA)**.
A intenção é **compartilhar conhecimento e facilitar o acesso** a materiais abertos e de qualidade técnica, estimulando contribuições que aprimorem o formato, usabilidade e integração com novas tecnologias.

> Se você também acredita que ciência e tecnologia evoluem melhor **com código aberto e cooperação**, este projeto é para você. 💡🤝

