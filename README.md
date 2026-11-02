# design-ON1X

Biblioteca de componentes HTML do design system.

**Acesse:** https://caiogbdesign.github.io/design-ON1X/

Os componentes aparecem em uma grade. Clique em **editar** em um deles, ajuste os knobs e use **Copiar HTML** para colar no Claude Design, ou **Aplicar** para ver o resultado na grade.

## Como adicionar um componente

1. Crie um arquivo em `components/`, por exemplo `components/alert.html`, com o `<style>` e o HTML do componente.
   Use valores fixos no CSS, com o estilo do Light em regras `[data-theme="light"]`, e marque os trechos editáveis com `{{nome}}`.
   Todos ficam na mesma página, então prefixe as classes com o nome do componente, como `.alert-warning .title`, para um não afetar o outro.
2. Adicione uma entrada em `components.json`:

```json
{
  "id": "alert",
  "name": "Alert",
  "category": "Feedback",
  "file": "components/alert.html",
  "description": "Mensagem de aviso.",
  "knobs": [
    { "name": "text", "label": "Texto", "type": "text", "default": "Algo deu certo." },
    { "name": "tone", "label": "Tom", "type": "select", "options": ["success", "danger"], "default": "success" }
  ]
}
```

   Para o componente aparecer na grade, acrescente `"grid": { "title": "Alert" }`. O `"values"` opcional muda como ele aparece ali, por exemplo `"values": { "bottomLeft": false }`. O `"options"` opcional cria o select da célula, por exemplo `"options": [{ "id": "glow-small", "label": "Glow" }]`. O `"group"` define o grupo no menu da lateral (Feedback, Ações, Formulários ou Exibição; sem ele, vai para Outros), e o `"navTitle"` opcional troca o nome mostrado ali.
   Para partes opcionais, use um knob `"type": "toggle"` (com `"default": true` ou `false`) e envolva o trecho com `{{#nome}}...{{/nome}}`.
   Ele só aparece, inclusive no "Copiar HTML", com o toggle ligado. `{{^nome}}...{{/nome}}` faz o contrário.
   Um knob com `"when": "nome"` só aparece no painel enquanto esse toggle estiver ligado.
   Um campo com `"hideLabel": true` logo depois de um toggle aparece na mesma linha dele.
3. Faça o commit. O site se atualiza sozinho em cerca de 1 minuto.

## Tokens

As cores da sessão Cores ficam em `colors.json`. Em `palette` vai o hex de cada tom; em `groups`, cada cor aponta para um tom da paleta em `dark` e `light`, ou traz o hex direto quando não tem primitiva, com `opacity` opcional, e traz a `description` mostrada na tabela.

O arquivo `tokens.css` guarda cores, fontes, raios e espaçamentos, mas o site não o carrega mais, e nenhum componente usa essas variáveis.
