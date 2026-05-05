# k1 WebAR com A-Frame + AR.js

Projeto WebAR simples e funcional para exibir uma logo 3D `k1` em realidade aumentada usando o marcador Hiro. A logo foi criada inteiramente no HTML com primitivas 3D do A-Frame, sem backend, sem React e sem modelos `.glb` externos.

Esta revisao usa uma configuracao mais segura para mobile:

- `A-Frame 1.3.0`
- `AR.js 3.4.5`
- apenas uma cena AR
- apenas um marcador
- apenas uma inicializacao de camera

## Arquivos

- `index.html`: cena WebAR completa com camera, marcador Hiro, luzes, overlay de instrucao e logo 3D `k1`.
- `README.md`: instrucoes de uso, publicacao e ajustes.

## Como abrir o projeto

Como o projeto usa camera no navegador, ele deve ser servido por HTTPS em uma hospedagem estatica para funcionar direito no celular.

Para uma checagem rapida no computador:

1. Abra o arquivo `index.html` em um navegador moderno.
2. Permita acesso a camera se o navegador solicitar.
3. Mostre o marcador Hiro para a camera.

Observacao:
Em muitos celulares, abrir o HTML diretamente pelo gerenciador de arquivos pode nao funcionar corretamente por causa das permissoes de camera. Para teste real no celular, publique em HTTPS.

## Como publicar

O projeto e estatico, entao funciona muito bem em:

- Netlify
- Vercel
- GitHub Pages

Basta publicar os dois arquivos na raiz do site:

1. `index.html`
2. `README.md`

### Netlify

1. Crie um novo site.
2. Envie a pasta do projeto.
3. Aguarde o deploy.
4. Abra a URL HTTPS gerada no celular.

### Vercel

1. Crie um novo projeto.
2. Importe a pasta ou repositorio.
3. Faca o deploy sem configuracao adicional.
4. Abra a URL HTTPS gerada no celular.

### GitHub Pages

1. Suba os arquivos para um repositorio.
2. Ative o GitHub Pages na branch principal.
3. Abra a URL publicada pelo GitHub Pages no celular.

## Por que precisa de HTTPS

No celular, o navegador normalmente so libera acesso a camera em:

- `https://`
- `localhost` em ambiente local

Como AR.js depende da camera para detectar o marcador, sem HTTPS a experiencia pode falhar, a camera pode nem abrir ou pode ser encerrada pelo navegador.

## Como imprimir o marcador Hiro

Use o marcador padrao Hiro do AR.js. Voce pode imprimir esta imagem:

- [Marcador Hiro oficial](https://raw.githubusercontent.com/AR-js-org/AR.js/master/data/images/hiro.png)

Dicas:

1. Imprima em papel branco com boa nitidez.
2. Evite dobrar o papel.
3. Use iluminacao razoavel.
4. Um tamanho entre 8 cm e 15 cm costuma funcionar bem.

## Como ajustar tamanho, posicao e rotacao da logo

A logo esta dentro do elemento:

```html
<a-entity id="k1-logo" position="0 0.24 0" rotation="-90 0 0" scale="0.72 0.72 0.72">
```

Voce pode ajustar:

- `position`: move a logo sobre o marcador.
- `rotation`: gira a logo.
- `scale`: aumenta ou diminui o conjunto.

Exemplos:

- Aumentar a logo:

```html
scale="1.15 1.15 1.15"
```

- Subir mais a logo:

```html
position="0 0.45 0"
```

- Girar a logo:

```html
rotation="-90 20 0"
```

Se quiser alterar partes especificas da letra `k` ou do numero `1`, edite os `a-box` dentro de `#k1-logo`.

## Como testar no celular

1. Publique o projeto em uma URL HTTPS.
2. Abra o link no navegador do celular.
3. Permita o uso da camera.
4. Imprima ou mostre o marcador Hiro em outra tela.
5. Aponte a camera para o marcador.
6. Quando o marcador for reconhecido, a logo `k1` aparecera em cima dele.

## Observacoes tecnicas

- O projeto usa `A-Frame` para renderizacao 3D declarativa.
- O projeto usa `AR.js` com `preset="hiro"` para reconhecimento do marcador.
- As versoes fixadas no HTML sao `A-Frame 1.3.0` e `AR.js 3.4.5`.
- A logo foi criada com `a-box`, sem assets 3D externos.
- A cena foi pensada para funcionar em navegador mobile sem backend.
- O HTML mostra uma mensagem de erro se a camera nao for liberada ou se a pagina nao estiver em contexto seguro.
