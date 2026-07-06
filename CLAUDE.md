# Thobias Pro — Contexto para Claude Code

## Stack
- Single-file HTML (thobias_pro_v51.html) — CSS e JS embutidos, vanilla JS, sem frameworks
- PWA com Service Worker (sw.js, estratégia network-first) e manifest.json
- Persistência: localStorage, chave fixa `thobias_v51` (nunca mudar sem migração)

## Regras críticas
- Nunca reescrever o app do zero — ler o código completo antes de editar; mudanças cirúrgicas apenas, preservando tudo que não foi explicitamente solicitado
- Nome do arquivo HTML nunca muda (`thobias_pro_v51.html`); versão fica só no `<title>` e no header do app
- IDs de itens (suplementos `sXX`, dermatologia `dXX`) nunca são reutilizados — sempre o próximo sequencial
- Mudança de estrutura de dados no localStorage exige migração automática (detectar chave antiga, migrar dados, apagar a antiga)
- Ao bumpar versão: atualizar `<title>`, versão exibida no header, e `const V` no sw.js se a mudança for significativa
- Antes de finalizar: validar chaves/divs balanceados no HTML/CSS/JS; confirmar que `save()` e `load()` funcionam com dados já existentes no localStorage

## Fluxo de entrega
1. Ler o arquivo atual do repositório antes de editar (nunca partir de versão em cache ou reconstruída de memória)
2. Aplicar a edição solicitada
3. Validar integridade (chaves, divs, sintaxe JS)
4. `git add`, commit com mensagem descritiva, `git push`
