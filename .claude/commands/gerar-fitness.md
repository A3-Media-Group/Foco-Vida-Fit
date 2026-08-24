Gere 5 novos artigos e 2 novas receitas para o blog Foco Vida Fit, seguindo o padrão dos artigos e receitas já existentes no projeto (leia 1-2 exemplos existentes antes de começar, para manter consistência de estrutura, tom de voz e formatação).

## Etapa 1 — Pesquisa de pauta
Pesquise na internet os temas de fitness, saúde e nutrição mais relevantes agora, cobrindo fontes do Brasil e de fora do Brasil. Verifique o que já existe no site para não duplicar assunto. Divida os 5 artigos assim:
- 2 artigos baseados nos temas historicamente MAIS BUSCADOS sobre fitness/saúde/nutrição (temas evergreen de alto volume de busca).
- 3 artigos baseados em temas ATUAIS/em alta no momento (tendências recentes, novidades de estudos, assuntos do momento na área fitness/saúde/nutrição).
Distribua entre categorias diferentes (emagrecimento, treino, nutrição, suplementação, saúde geral, etc.) para não concentrar tudo no mesmo tema.

## Etapa 2 — Escrever os 5 artigos
Para cada artigo:
- Mínimo 1000–1500 palavras, H1 único, H2/H3 organizando o conteúdo, introdução, conclusão, e seção de perguntas frequentes quando fizer sentido.
- Meta title (até 60 caracteres) e meta description (até 155 caracteres) otimizados para SEO.
- Basear todas as informações em fontes oficiais e confiáveis, combinando fontes brasileiras (Ministério da Saúde, ANVISA, Sociedade Brasileira de Endocrinologia, Sociedade Brasileira de Medicina do Esporte) e internacionais (OMS/WHO, USDA, estudos revisados por pares/PubMed), sempre parafraseando, nunca copiando texto de fontes externas.
- Escrever de forma otimizada para monetização com Google AdSense: conteúdo aprofundado e original, sem clickbait enganoso, sem promessas milagrosas, sem alegações sem embasamento, com boa estrutura para retenção de leitura (parágrafos curtos, listas, subtítulos).
- Incluir aviso de que o conteúdo é informativo e não substitui orientação médica/nutricional individual.
- Adicionar 2 a 4 links internos para artigos ou receitas já existentes no site que sejam relevantes.
- Categorizar corretamente conforme as categorias já existentes.
- Aplicar dados estruturados (schema Article, e FAQPage se houver perguntas frequentes).
- URL amigável em português, seguindo o padrão das URLs já existentes.

## Etapa 3 — Escrever as 2 receitas
Para cada receita:
- Nome atrativo, tempo de preparo, rendimento, informação nutricional aproximada (calorias, proteína, carboidrato, gordura), lista de ingredientes, modo de preparo passo a passo, e dica de substituição de ingrediente (ex: versão vegana ou sem glúten).
- Aplicar dados estruturados (schema Recipe).
- Cobrir momentos diferentes das receitas já existentes no site.

## Etapa 4 — Buscar imagens reais
Para cada um dos 5 artigos e das 2 receitas:
- Busque na internet uma foto real (não ilustração, não gerada por IA) que reflita exatamente o tema específico daquele conteúdo, não uma imagem genérica.
- Use bancos de imagens gratuitos e de uso comercial permitido, como Unsplash, Pexels e Pixabay.
- Confirme que a licença permite uso comercial sem exigir atribuição obrigatória (se exigir, anote para o usuário adicionar o crédito).
- Baixe e salve a imagem na pasta de assets/imagens correta do projeto, com nome de arquivo descritivo em português.
- Garanta que a imagem tenha pelo menos 1200x630 pixels, para funcionar bem também como og:image.
- Adicione texto alternativo (alt text) descritivo em português.
- Otimize/comprima a imagem sem perda visível de qualidade.

## Etapa 5 — Integração
- Adicione os 5 artigos e as 2 receitas nos locais corretos do site (listagens, home se aplicável, sitemap.xml).
- Data de publicação (obrigatório): use SEMPRE a data real atual do sistema no fuso America/Sao_Paulo (nunca uma data manual, fixa, futura ou retroativa) para: o campo `date` em `site-data.js` (tanto ARTICLES quanto RECIPES), a linha "Atualizado em" e o atributo `date` do TrustBadge em cada página, e os campos `datePublished`/`dateModified` do schema JSON-LD (formato "DD mmm AAAA" em português para os campos visíveis, ISO "AAAA-MM-DD" no JSON-LD). Atualize também o `date="..."` de qualquer card relacionado (ArticleCard) em outras páginas que aponte para o novo conteúdo.
- Atualize o sitemap.xml para incluir as novas páginas, com `<lastmod>` também na data real atual (formato ISO "AAAA-MM-DD").
- Ao final, mostre uma lista com: título de cada artigo/receita, se é "mais buscado" ou "tema atual" (no caso dos artigos), categoria, data de publicação usada, e a fonte de cada imagem usada.

Depois de gerar e integrar tudo corretamente, rode o preview local para confirmar que não quebrou nada. Se estiver tudo certo, faça commit dessas mudanças com uma mensagem descritiva (ex: 'Adiciona 5 artigos e 2 receitas via gerar-fitness') e envie (push) automaticamente para o GitHub, sem pedir confirmação.
