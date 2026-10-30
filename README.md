# design-ON1X

Biblioteca de componentes HTML do design system.

**Acesse:** https://caiogbdesign.github.io/design-ON1X/

Escolha um componente na lateral, ajuste os knobs e clique em **Copiar HTML** para colar no Claude Design.

## Como adicionar um componente

1. Crie um arquivo em `components/`, por exemplo `components/alert.html`, com o `<style>` e o HTML do componente.
   Use as variáveis de `tokens.css` (`var(--ds-primary)` etc.) e marque os trechos editáveis com `{{nome}}`.
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

   O `category` define a pasta na lateral. Use `/` para criar subpastas, por exemplo `"Botões / Glow"`.
   Para partes opcionais, use um knob `"type": "toggle"` (com `"default": true` ou `false`) e envolva o trecho com `{{#nome}}...{{/nome}}`.
   Ele só aparece, inclusive no "Copiar HTML", com o toggle ligado. `{{^nome}}...{{/nome}}` faz o contrário.
   Um knob com `"when": "nome"` só aparece no painel enquanto esse toggle estiver ligado.
3. Faça o commit. O site se atualiza sozinho em cerca de 1 minuto.

## Tokens

Cores, fontes, raios e espaçamentos ficam em `tokens.css`, com tema claro em `:root` e escuro em `[data-theme="dark"]`.
