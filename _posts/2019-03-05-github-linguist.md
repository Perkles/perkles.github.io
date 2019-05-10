---
date: 2019-03-03
title: Porque meu repositório no Github aparece com a linguagem errada ?
layout: posts
author: Otávio Reis Perkles
comments: true
---


![Linguist](/assets/images/octocat.png){:class="title-image"}

___

Já se perguntou porque as vezes quando subimos um novo projeto no Github aquela barrinha aparece com a proporção errada da linguagem ? Basta adicionar o Bootstrap no seu repositório e automaticamente todo o projeto é rotulado como JavaScript? 
Pois é ... isso acontece porque o github usa uma biblioteca chamada de [Linguist](https://github.com/github/linguist) (Linguista) que identifica a linguagem empregada em cada arquivo e em seguida gera uma porcentagem usada para montar aquele gráfico que encontramos em cima de nossos repositórios.

### Porque eu devo me importar ?

Bom eu me importo porque eu sou ~~otário~~ detalhista e gosto que as coisas estejam apresentadas da melhor forma possível, ainda mais quando o assunto diz respeito ao código que escrevo. O Github também é usado por muitos para checar o que você tem produzido, se tem contribuído para projetos Open Source ou simplesmente para _stalkear_. Porém o Headhunter de uma empresa te _stalkeando_ possui mais relevância do que sua ex-namorada,  certo ? 
Por isso vou explicar aqui como falar a 'língua' do Linguista e deixar a 'casa' sempre arrumada. :smiley:

O Github não é burro, não é que ele entende errado o que vc quis dizer com seu projeto web em Java. O problema é que não falamos o que queríamos da forma clara possível. 'O computador faz exatamente o que mandamos ele fazer'

Logo para dizer ao Linguista qual linguagem de fato estamos usando é preciso deixar bem claro. Fazemos isso através do arquivo ```.gitattributes``` mapeando caminhos ou extensões com seu respectivo conjunto 'chave'. 
Assim podemos classificar código dentro do Linguista em cinco categorias:

 - ```linguist-vendored.```
 - ```linguist-documentation.```
 - ```linguist-generated.```
 - ```linguist-detectable.```
 - ```linguist-language.```

### Código de 'terceiros'

Pode ser usado para demarcar código de 'terceiros', ou seja, código que não foi necessariamente escrito por você. Bootstrap e JQuery são exemplos de tais bibliotecas que podem fazer com que as estatísticas de linguagem do seu repositório fiquem infladas com Javascript, HTML e CSS e podem até mesmo causar uma rotulação errada do mesmo. O linguista trata todos os caminhos contidos em [vendor.yml](https://github.com/github/linguist/tree/master/vendor) como de terceiros e ja não os incluem nas estatísticas de linguagem do reporitório.

Use o atributo para marcar ou desmarcar tais códigos como de 'terceiros':

```
assets/js/terceiros/* linguist-vendored
jquery.js linguist-vendored=false
```

### Documentação

Assim como código produzido por terceiros (vendored) o linguista exclue das estatísticas caminhos comuns usados para documentação que se encontram em [documentation.yml](https://github.com/github/linguist/blob/master/lib/linguist/documentation.yml).

Use a marcação ```linguist-documentation``` para marcar ou desmarcar caminhos como documentação.

```
project-docs/* linguist-documentation
docs/formatter.rb linguist-documentation=false
```

### Código gerado

Arquivos gerados como JavasCript minificado e CoffeScript compilado também pode ser detectado e excluído dos status de seu repositório. 

Use ```linguist-generated``` para demarcar tais elementos.

```
Api.elm linguist-generated=true
```

### Código detectável.

Apenas linguagens de programação são incluídos nas estatísticas de linguagem. Linguagens de tipos diferentes das definidas em [languages.yml](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml) não são detectadas. 

Para você que é o diferentão e está sempre inventando algo, use ```linguist-detectable``` para demarcar seu código como detectável. 

```
*.kicad_pcb linguist-detectable=true
*.sch linguist-detectable=true
tools/export_bom.py linguist-detectable=false
```

### Como vou além ?

Você ainda pode rodar o linguista no seu computador e ter estatísticas mais apuradas das linguagens utilizadas em seus repositórios, para isso você pode conferir a [instalação](https://github.com/github/linguist#installation) diretamente na documentação do Linguist. 


## Bonus 

Bom, agora que você sabe como organizar de forma efetiva as linguagens em seus repositórios, agora que sabem também a importância disso para sua carreira e para as estatísticas globais do Github. Que tal conhecer o [Sourcerer](https://sourcerer.io/) ? 
É um site que gera estatísticas super legais baseadas em sua atividade no Github. Você pode usar apenas como curiosidade ou profissionalmente, fique a vontade.

![Sourcerer](/assets/images/sourcerer.png){:class="title-image"}














