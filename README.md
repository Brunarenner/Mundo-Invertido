# 🌑 Mundo Invertido — README

> Um site estático que recria a atmosfera sombria do "Mundo Invertido" inspirado em *Stranger Things*. Feito com HTML, CSS (variáveis para temas claro/escuro) e estrutura acessível. Este README foi pensado para ser didático, com ilustrações e instruções claras para rodar e personalizar o projeto.

---

## 🧭 Visão geral

O projeto apresenta:

* Uma **capa (header)** com arte e texto de apresentação.
* Dois temas: **light-theme** e **dark-theme** (controlados por classes no `body`).
* Seções: descrição, trailer (embed do YouTube), galeria de imagens, formulário de inscrição e footer.
* Efeitos visuais com `mask` / `-webkit-mask` para imagens decorativas.

---

## 📁 Estrutura de pastas (exemplo)

```
mundo-invertido/
├─ index.html
├─ assets/
│  ├─ css/
│  │  └─ styles.css
│  ├─ img/
│  │  ├─ mundo-i.png
│  │  ├─ invert-img.png
│  │  ├─ 01.png
│  │  ├─ 02.png
│  │  ├─ 03.png
│  │  ├─ bicicleta.png
│  │  ├─ monstro.png
│  │  ├─ lam.png
│  │  └─ lam-invertidas.png
│  └─ audio/
│     └─ j.wav
└─ README.md
```

---

## 🎯 Objetivos do README

1. Explicar como rodar o projeto localmente.
2. Mostrar como ativar a troca de tema (light / dark).
3. Ajudar a personalizar imagens, cores e textos.
4. Apontar observações de acessibilidade e correções úteis encontradas no CSS.

---

## 🚀 Como abrir localmente

1. Clone ou baixe o repositório para sua máquina.
2. Abra o arquivo `index.html` no navegador (duplo clique ou `Live Server` no VS Code).

**Dica (recomendado):** usar `Live Server` do VS Code para evitar problemas com paths relativos e para desenvolvimento.

---

## 🛠️ Como adicionar a funcionalidade de troca de tema

No HTML há um botão com `onclick="switchTheme()"`. Abaixo um script simples (adicione antes do fechamento de `</body>`):

```html
<script>
  function switchTheme(){
    const body = document.body;
    if(body.classList.contains('light-theme')){
      body.classList.remove('light-theme');
      body.classList.add('dark-theme');
    } else {
      body.classList.remove('dark-theme');
      body.classList.add('light-theme');
    }
  }

  // Exemplo: tocar áudio ao mudar tema (opcional)
  const audio = document.querySelector('header audio');
  document.getElementById('switch-theme-button').addEventListener('click', () => {
    if(audio) { audio.currentTime = 0; audio.play().catch(()=>{/* autoplay poderia ser bloqueado */}); }
  });
</script>
```

---

## 🎨 Variáveis CSS e personalização rápida

No `styles.css` o projeto usa `:root` sob classes `.light-theme` e `.dark-theme` para definir variáveis como `--page-background`, `--primary-color`, `--highlight-color`, etc. Alterando essas variáveis você muda o visual global com facilidade.

**Exemplos úteis que você pode editar:**

* `--primary-color` — cor de destaque (botões, bordas).
* `--highlight-color` — cor de fundo/borda das imagens.
* `--background-lamp-image` — imagem de background da galeria.
* `--character-top-image-src` e `--character-bottom-image-src` — usados com `mask`/`-webkit-mask`.

---

## 🧩 Notas sobre o CSS (observações e correções encontradas)

* O código já contém comentários de correção — por exemplo, a correção de `inout` para `input` em regras de fontes.
* As propriedades de `mask` usam variáveis para os `url(...)`. Verifique se os caminhos em `--character-top-image-src` e `--character-bottom-image-src` apontam corretamente para `assets/img/` (no CSS estão como `../img/*.png` — adapte para `../assets/img/*.png` se necessário, dependendo de onde o CSS estiver).
* A declaração `linear-gradient` na `.dark-theme` tem quebra de linha — o valor deverá estar sem quebras estranhas para evitar erros:

```css
--page-background: linear-gradient(180deg, #050000 0%, #130404 65%, rgba(19, 1, 1, 0.75) 100%);
```

* Prefira usar `object-fit: cover` nas imagens da galeria (já usado) para garantir proporção adequada.

---

## ♿ Acessibilidade

* Use `alt` descritivo nas imagens (já presente, mas revise para descrever o conteúdo da imagem).
* Seções importantes têm `role` em alguns elementos; você pode melhorar adicionando `aria-labelledby` e `aria-describedby` quando aplicar formulários e seções interativas.
* Para o formulário, adicione `type="email"` no campo de e-mail e `type="tel"` para telefone para melhorar a experiência em mobile e validação.

Exemplo:

```html
<input type="email" name="email" id="txtEmail" required>
<input type="tel" name="telefone" id="txtTel" pattern="[0-9\-\s]+">
```

---

## 🖼️ Ilustrações e imagens (para README)

Abaixo alguns exemplos de como você pode inserir imagens no README do GitHub (use este formato com caminhos relativos):

```markdown
![Capa do Mundo Invertido](assets/img/mundo-i.png)
![Ilustração principal](assets/img/invert-img.png)
![Galeria - item 1](assets/img/01.png)
```

> 💡 Se for disponibilizar imagens maiores, deixe uma pasta `assets/screenshots/` com PNGs otimizados para mostrar no README.

---

## ✅ Boas práticas e sugestões

* Otimize imagens (imagem muito grandes impactam o carregamento). Use o formato WebP quando possível.
* Separe estilos específicos de impressão se quiser suporte para imprimir a página.
* Centralize variáveis de cor no topo do CSS para facilitar theming.
* Documente eventuais dependências (ex.: fontes externas em `index.html`).

---

## 🛎️ Exemplo de README visual (se quiser copiar e colar no GitHub)

> Use as imagens reais do projeto para o visual

```markdown
# Mundo Invertido

![Capa](assets/img/mundo-i.png)

Uma página estática que recria a estética do Mundo Invertido com temas claro/escuro e componentes: trailer, galeria e formulário.

## Como rodar
1. Abrir `index.html` em um navegador.
2. (Opcional) usar `Live Server`.

## Trocar tema
Clique no botão `Inverter Mundos` para alternar entre light e dark (JS simples necessário).
```

---

## ✍️ Contribuindo

1. Fork este repositório.
2. Crie uma branch: `git checkout -b feature/minha-mudanca`.
3. Faça as mudanças e abra um Pull Request com descrição clara.

---

## 📜 Licença

Escolha uma licença (ex.: MIT) e adicione um arquivo `LICENSE` no repositório.

---

