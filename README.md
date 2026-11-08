# AnimeStats Lab

**AnimeStats Lab** é um projeto pessoal de descoberta, comparação e organização de animes, desenvolvido em português brasileiro (PT-BR). Prioriza a **popularidade em members do MyAnimeList** e usa notas e avaliações como métricas complementares.

**Página pública:** https://ytacoixao.github.io/animestats-lab/  
**Documentação para IAs:** https://ytacoixao.github.io/animestats-lab/llms.txt  
**Referência detalhada:** https://ytacoixao.github.io/animestats-lab/ai-guide.html  
**Informações estruturadas:** https://ytacoixao.github.io/animestats-lab/project-info.json

## Distinção essencial: site público vs. aplicativo local

A página do **GitHub Pages** é uma apresentação e documentação pública do projeto. **Não hospeda o painel funcional nem disponibiliza a API privada do computador.**

O aplicativo funcional é iniciado localmente por **INICIAR-ANIMESTATS.bat** (Python + JavaScript) e abre em **http://127.0.0.1:8765** no computador em que estiver rodando. Esse endereço **não é um site público**.

Este repositório contém a página institucional e a documentação pública. Não presuma que os arquivos do aplicativo local completo estejam disponíveis aqui. Não há chatbot de IA na versão atual.

## Recursos já implementados no aplicativo local

- Ranking e pesquisa de anime via **API oficial MyAnimeList v2**.
- Prioridade aos **members** (campo `num_list_users`), não apenas à média de notas.
- Carregamento progressivo: amostra inicial de até **500 entradas** e lotes de 100; possibilidade de rolagem automática.
- Ordenação por members, nota MAL, quantidade de avaliações, ranking, nota ajustada ou índice de impacto experimental.
- Filtros de gênero, formato, mínimo de members e situação de dublagem PT-BR.
- Informações de dublagem da **AniDub** (fonte comunitária, com incertezas; sem registro não significa ausência de dublagem).
- Favoritos mantidos **no banco SQLite local**.
- Um cartão por série quando temporadas são identificadas; ficha reúne prequelas e sequências do MAL, com dados **por temporada**. OVAs, spin-offs e remakes não são necessariamente agrupados.
- Sinopses traduzidas automaticamente para PT-BR sob demanda, com opção de narração por voz do navegador quando uma voz adequada está disponível.
- Galeria com até **cinco artes visuais** (fanarts, banners, pôsteres e artes alternativas), sem miniaturas de episódios; AniZip/TheTVDB e MAL.

## O que significam as métricas

- **Members / `num_list_users`:** usuários que adicionaram o título à própria lista MAL. **Não** é o número de avaliações nem o número de pessoas que comprovadamente assistiram.
- **Avaliações / `num_scoring_users`:** usuários que deram nota.
- **Nota MAL / `mean`:** média publicada pelo MyAnimeList.
- **Índice de impacto opcional:** `log10(members + 1) × (mean / 10)`. É um indicador experimental, não um ranking oficial do MAL.
- **Temporadas agrupadas:** o aplicativo **não soma members** entre temporadas, pois uma pessoa pode aparecer em mais de uma lista.

## Arquitetura resumida

- **Backend local:** Python `http.server`, `requests`, SQLite; host `127.0.0.1`, porta `8765`.
- **Frontend local:** HTML, CSS e JavaScript.
- **Fontes externas:** MyAnimeList v2 (dados de anime), AniDub (status comunitário de dublagem), AniZip/TheTVDB e MAL (artes), tradução automática não oficial quando solicitada.
- **Persistência:** cache e favoritos no SQLite local; Client ID MAL salvo somente no computador do usuário.
- **Privacidade:** nunca publicar chaves, banco local, favoritos de uma pessoa, sinopses privadas ou dados pessoais. Não há endpoints locais expostos publicamente.

## Para assistentes de IA e desenvolvedores

Comece por [llms.txt](https://ytacoixao.github.io/animestats-lab/llms.txt), [ai-guide.html](https://ytacoixao.github.io/animestats-lab/ai-guide.html) e [project-info.json](https://ytacoixao.github.io/animestats-lab/project-info.json). A página pública descreve o projeto; **não permite consultar automaticamente os favoritos privados do usuário ou executar ações no app local**.

**Ideias futuras, ainda não integradas:** recomendações explicadas por IA e chat de busca natural usando modelos em nuvem. Não afirme que esses recursos já existem.

## Situação e atribuições

Projeto independente, não comercial, sem afiliação ou endosso pelo MyAnimeList, AniDub ou TheTVDB. Os serviços e dados de terceiros seguem seus próprios termos.

Última atualização da documentação: **8 de novembro de 2026**.
