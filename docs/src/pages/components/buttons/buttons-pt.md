---
title: Componente React para Botão
components: Button, IconButton, ButtonBase
---

# Botão

<p class="description">Botões permitem que os usuários tomem ações e decisões com um simples toque.</p>

[Botões](https://material.io/design/components/buttons.html) comunicam ações que os usuários podem realizar. Eles são normalmente colocados em toda a interface do usuário, em lugares como:

- Caixa de diálogo
- Janelas modais
- Formulários
- Cartões
- Barras de ferramentas

## Botões Contidos

[Botões Contidos](https://material.io/design/components/buttons.html#contained-button) tem alta ênfase, distinguem-se pelo uso de elevação e preenchimento. Eles contém as principais ações da sua aplicação.

{{"demo": "pages/components/buttons/ContainedButtons.js"}}

Você pode remover a sombra com a propriedade `disableElevation`.

{{"demo": "pages/components/buttons/DisableElevation.js"}}

## Botões de Texto

[Botões de texto](https://material.io/design/components/buttons.html#text-button) são utilizados tipicamente para ações menos-pronunciadas, incluindo aquelas localizadas em:

- Caixas de diálogo
- Cartões

Em cartões, os botões de texto ajudam a manter a ênfase no conteúdo do cartão.

{{"demo": "pages/components/buttons/TextButtons.js"}}

## Botões Delineados

[Botões delineados](https://material.io/design/components/buttons.html#outlined-button) são botões com ênfase média. Eles contém ações que são importantes, mas não são as ações primárias de um aplicativo.

Botões delineados são uma alternativa de menor ênfase comparado com botões contidos, ou uma uma alternativa de maior ênfase comparado com botões de texto.

{{"demo": "pages/components/buttons/OutlinedButtons.js"}}

## Botão de Upload

{{"demo": "pages/components/buttons/UploadButtons.js"}}

## Tamanhos

Gosta de botões maiores ou menores? Use a propriedade `size`.

{{"demo": "pages/components/buttons/ButtonSizes.js"}}

## Botões com ícones e rótulo

Às vezes você pode querer ter ícones para determinados botão para melhorar o UX do aplicativo como reconhecemos logotipos mais facilmente do que o texto sem formatação. Por exemplo, se você tem um botão com a açõo de "deletar" você pode rotulá-lo com um ícone do caixote de lixo.

{{"demo": "pages/components/buttons/IconLabelButtons.js"}}

## Botões de Ícone

Botões de ícones são comumente encontrados em barras de aplicativos e barras de ferramentas.

Ícones são também adequadas para botões de alternância que permitem uma escolha única para ser selecionado ou desmarcada, como adicionar ou remover uma estrela para um item.

{{"demo": "pages/components/buttons/IconButtons.js"}}

## Botões Personalizados

Aqui estão alguns exemplos de customização do componente. Você pode aprender mais sobre isso na [página de documentação de sobrescritas](/customization/components/).

{{"demo": "pages/components/buttons/CustomizedButtons.js", "defaultCodeOpen": false}}

👑 Se você está procurando inspiração, você pode verificar [os exemplos de customização de MUI Treasury](https://mui-treasury.com/components/button).

## Botões Complexos

O botões de texto, botões contidos, botões de ação flutuante e ícone botões são construídos em cima do mesmo componente: O componente `ButtonBase `. Você pode tirar vantagem deste componente de nível mais abastrato para construir interações personalizadas.

{{"demo": "pages/components/buttons/ButtonBase.js"}}

## Biblioteca de roteamento de terceiros

Um caso de uso comum é usar o botão para acionar uma navegação para uma nova página. O componente `ButtonBase` fornece uma propriedade para lidar com este caso de uso: `componente`. No entanto, para alguns polyfills de foco `ButtonBase` requer o nó DOM do componente fornecido. Isso é obtido anexando-se uma referência ao componente e esperando que o componente envie essa referência para o nó DOM subjacente. Dado que muitos dos componentes interativos dependem do `ButtonBase`, você deve ser capaz de tirar proveito em todos os lugares.

Aqui está um [exemplo de integração com react-router](/guides/composition/#button).

## Limitações

### Cursor não permitido

O componente ButtonBase define `pointer-events: none;` ao desabilitar os botões, o que previne que o cursor desabilitado seja exibido.

Se você deseja usar `not-allowed`, você tem duas opções:

1. ** apenas CSS**. Você pode remover o estilo dos eventos do ponteiro no estado "desabilitado" do elemento `<button>` :

  ```css
  .MuiButtonBase-root:disabled {
    cursor: not-allowed;
    pointer-events: auto;
  }
  ```

Contudo:

- Você deve adicionar `eventos-ponteiro: nenhum;` novamente quando você precisa exibir dicas [ ferramentas em elementos desabilitados](/components/tooltips/#disabled-elements).</li> 
    
    - O cursor não muda se você renderizar algum outro elemento de botão, por exemplo, um elemento link `<a>`.</ul> 
    
    2. ** Alteração no DOM** Você pode encapsular o botão:
    
      ```jsx
      <span style={{ cursor: 'not-allowed' }}>
        <Button component={Link} disabled>
          disabled
        </Button>
      </span>
      ```
    
    Isso tem a vantagem de suportar qualquer elemento, por exemplo, um elemento de link `<a>`.