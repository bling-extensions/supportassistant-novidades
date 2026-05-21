# supportassistant-novidades

Site de novidades por versão do **SupportAssistant**, publicado via GitHub Pages em:

**https://setradevelopment.github.io/supportassistant-novidades/**

## Estrutura

```
/
├── index.html              ← lista de versões publicadas
├── assets/
│   ├── style.css           ← identidade visual compartilhada
│   └── videos/             ← MP4s demonstrando cada feature
└── v1.6.8/
    └── index.html          ← página da v1.6.8
```

## Como adicionar uma versão nova

1. Duplicar a pasta da versão anterior: `cp -r v1.6.8 v1.6.9`
2. Editar `v1.6.9/index.html` (título, data, lista de features, nomes dos vídeos)
3. Adicionar o card da versão nova em `index.html` (no topo da lista)
4. Gravar os MP4s e jogar em `assets/videos/`
5. `git add . && git commit -m "v1.6.9: novidades" && git push`

## Gravando vídeo leve

Recomendação: capturar com OBS / ScreenToGif / Windows Game Bar, exportar como `.mov` ou `.mp4` bruto, depois otimizar:

```bash
ffmpeg -i bruto.mov -vcodec libx264 -crf 28 -preset slow -an -movflags +faststart saida.mp4
```

- `-crf 28`: qualidade boa pra demo (16-23 = alta qualidade, 28-32 = web)
- `-an`: sem áudio (não precisa pra demo)
- `-movflags +faststart`: web-otimizado (começa a tocar antes do download completar)
- Costuma sair 5-10x menor que GIF da mesma cena

## Convenção de nomes de arquivos de vídeo

`<feature>-<contexto>.mp4`, kebab-case, sem acentos. Exemplos:

- `resumo-atendimento.mp4`
- `aba-resumo-config.mp4`
- `atalhos-ctrl-bold.mp4`
- `variavel-turno.mp4`
- `variavel-complete.mp4`
