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

3. Faça o commit. O site se atualiza sozinho em cerca de 1 minuto.

## Tokens

Cores, fontes, raios e espaçamentos ficam em `tokens.css`, com tema claro em `:root` e escuro em `[data-theme="dark"]`.
