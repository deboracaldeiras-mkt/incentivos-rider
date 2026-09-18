# Incentivos Daki — hospedagem própria

Esse pacote tem só um arquivo (`index.html`) — o artefato completo, já com login
só por ID e busca em tempo real na planilha (via `apps-script-incentivos.gs`).
Publicando isso fora do Claude, não existe mais link congelado nem "versão
fantasma": o que estiver no seu repositório é exatamente o que os riders veem.

## Passo a passo — GitHub Pages (grátis, sem servidor)

1. **Crie um repositório novo** no GitHub (pode ser público ou privado — Pages
   funciona nos dois, mas repositório privado exige GitHub Pro/Team/Enterprise
   pra publicar Pages a partir dele).

2. **Suba o arquivo `index.html`** pra raiz do repositório:
   - Pela interface web: botão "Add file" → "Upload files" → arraste o
     `index.html` → "Commit changes".
   - Ou pelo terminal:
     ```bash
     git clone https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
     cp index.html SEU-REPOSITORIO/
     cd SEU-REPOSITORIO
     git add index.html
     git commit -m "Publica Incentivos Daki"
     git push
     ```

3. **Ative o GitHub Pages**: no repositório, vá em **Settings → Pages**.
   Em "Source", escolha **"Deploy from a branch"**, selecione a branch
   `main` (ou `master`) e a pasta `/ (root)`. Clique em **Save**.

4. **Espere 1–2 minutos.** O GitHub mostra a URL final no topo da mesma
   página de Settings → Pages, algo como:
   ```
   https://SEU-USUARIO.github.io/SEU-REPOSITORIO/
   ```
   Essa é a URL definitiva — é ela que você passa pros riders (ou coloca
   dentro do app RAIO via WebView, se chegarem a fazer essa integração).

5. **Teste**: abra a URL, faça login com um ID que exista na planilha e
   confirme que os dados batem com o que está lá.

## Atualizando depois

Qualquer alteração no artefato = subir um novo `index.html` no lugar do
antigo (ou `git push` de novo). O GitHub Pages atualiza automaticamente em
1–2 minutos, sem precisar mexer em configuração nenhuma de novo.

## O que continua igual, mudando de casa

- **A URL da API do Apps Script** já está fixa dentro do `index.html`
  (variável `SHEET_API_URL` no `<script>`) — não precisa reconfigurar nada.
- **A planilha e o Apps Script continuam exatamente onde estão.** Só o
  arquivo HTML (a "cara" do app) está mudando de endereço.
- **O CORS/JSONP continua funcionando igual**, já que a chamada é feita do
  navegador do rider pra sua API, independente de onde o HTML está hospedado.

## Se preferir Netlify em vez de GitHub Pages

Netlify é ainda mais simples pra um arquivo único: entre em
[app.netlify.com/drop](https://app.netlify.com/drop) e arraste a pasta
inteira (ou só o `index.html`) pra essa página. Ele publica na hora e te dá
uma URL pronta — sem precisar criar repositório Git.
