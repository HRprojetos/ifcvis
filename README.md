# Portal BIM IFC

Portal estático para visualizar e compartilhar projetos IFC usando GitHub + Vercel.

## Estrutura

- `index.html` — lista os projetos cadastrados.
- `viewer.html` — visualizador IFC 3D.
- `projects.json` — cadastro dos projetos e disciplinas.
- `models/` — coloque aqui os IFCs que serão publicados.
- `vercel.json` — configuração básica para deploy na Vercel.

## Publicar o primeiro projeto

1. Coloque os arquivos IFC em `models/`.
2. Edite `projects.json`.
3. Troque `published` para `true`.
4. Adicione os modelos no array `models`.

Exemplo:

```json
{
  "slug": "casa-joao",
  "title": "Residência João e Maria",
  "client": "João e Maria",
  "revision": "R03",
  "updated": "17/08/2026",
  "status": "EM APROVAÇÃO",
  "published": true,
  "models": [
    {
      "discipline": "Arquitetura",
      "url": "./models/casa-joao-arq.ifc"
    },
    {
      "discipline": "Estrutural",
      "url": "./models/casa-joao-est.ifc"
    }
  ]
}
```

O link compartilhável será:

`https://SEU-DOMINIO/viewer.html?project=casa-joao`

## Testar localmente

Como o portal usa `fetch()` para ler `projects.json`, não abra apenas com duplo clique no HTML. Inicie um servidor local na pasta, por exemplo:

```bash
python -m http.server 8000
```

Depois abra `http://localhost:8000`.

## Deploy na Vercel

1. Crie um repositório no GitHub.
2. Envie todos os arquivos desta pasta.
3. Importe o repositório na Vercel.
4. Framework Preset: `Other`.
5. Não é necessário comando de build.
6. Faça o deploy.

## Privacidade

Esta primeira versão é baseada em arquivos estáticos. Quem tiver o link do IFC publicado poderá tecnicamente acessar o arquivo. Para projetos privados, a próxima evolução deve usar autenticação + storage privado e entregar o modelo somente após validar a sessão.
