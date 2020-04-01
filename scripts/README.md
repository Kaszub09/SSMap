# Context Menu Javascript

Este é um guia do usuário que demonstra a utilização dessa lib.

Uma live preview pode ser visualizada [aqui](https://codepen.io/richardbranvo/pen/OJLqxWq)

## 1. Criando o menu

A estrutura do menu é composta por um tema e uma lista de itens. Cada item é composto por um icone (font awesome), um nome e uma ação a ser realizada.

```javascript
const menu = new ContextMenu(
  {
    'theme': 'default',
      'items': [
        {'icon': 'envelope', 'name': 'Enviar',  action: () => console.log('clicou enviar')  },
        {'icon': 'download', 'name': 'Baixar',  action: () => console.log('clicou baixar')  },
        {'icon': 'trash',    'name': 'Remover', action: () => console.log('clicou remover') },
      ]
  }
);

```

## 2. Adicionando o evento

Aqui informaremos que o documento deve escutar o evento de clique com o botão direito do mouse, mas o evento pode ser adicionado em qualquer elemento do dom.

```javascript
document.addEventListener('contextmenu', openContextMenu, false);
```

## 3. Criando a função de exibição do menu

```javascript
function openContextMenu(evt){
  // impede que o menu de contexto padrão do sistema seja aberto
  evt.preventDefault();
  
  // configura um pequeno delay para a abertura do novo menu caso o mesmo esteja aberto
  const time = menu.isOpen() ? 100 : 0;

  // esconde o menu atualmente ativo (se existir)
  menu.hide();

  // exibe o menu na posição clicada pelo mouse
  setTimeout(() => { menu.show(evt.pageX, evt.pageY) }, time);

  // configura um novo escutador que fecha o menu caso o usuário clique em qualquer lugar da tela
  document.addEventListener('click', hideContextMenu, false);
}
```

## 4. Criando a função de fechamento do menu

```javascript
function hideContextMenu(evt){
  // esconde o menu
  menu.hide();
  
  // remove o escutador do documento
  document.removeEventListener('click', hideContextMenu);
}
```