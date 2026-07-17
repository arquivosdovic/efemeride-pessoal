# Efeméride Pessoal

Calculadora de mapa natal e trânsitos astrológicos, feita para uso pessoal. Roda 100% no navegador — um único arquivo HTML, sem backend, sem instalação, sem envio de dados para servidor nenhum.

A ideia central: você calcula e organiza seus próprios trânsitos (com casa, signo, grau e aspecto) antes de levar isso a alguém — ou a uma IA — para interpretar. Os resultados podem ser exportados em texto pronto para colar num assistente de IA.

## Funcionalidades

- **Mapa natal**: signo, grau e casa de Sol, Lua, Mercúrio, Vênus, Marte, Júpiter, Saturno, Urano, Netuno, Plutão, Quíron, Nodo Norte, Ascendente e Meio do Céu.
- **Trânsitos**:
  - **Data única** — posição de cada planeta e todos os aspectos formados com o mapa natal num momento específico. Botão "Preencher com agora" pega a data/hora/fuso atuais do seu computador.
  - **Intervalo / ano** — varre um período (um ano, vários anos) e lista as janelas de cada aspecto: início, data exata (orbe mínimo) e fim.
- **Sistemas de casas**: Signos Inteiros, Casas Iguais e Placidus (cálculo iterativo por trisecção do arco semi-diurno/noturno; se a latitude for extrema demais para o método convergir, o sistema avisa e usa Casas Iguais como alternativa).
- **Busca de cidade**: campo de busca (via OpenStreetMap/Nominatim) que preenche latitude/longitude automaticamente. O fuso horário continua manual — regras de horário de verão mudam por época e país, então não é seguro automatizar isso silenciosamente.
- **Importar/exportar dados de entrada**: os dados do mapa natal (data, hora, fuso, latitude, longitude, sistema de casas) podem ser exportados como JSON e reimportados depois — colando o texto ou subindo o arquivo — para não ter que preencher tudo de novo a cada uso.
- **Filtros**: por planeta em trânsito, signo, casa natal, tipo de aspecto, ponto natal e impacto mínimo (0–100).
- **Ordenação por impacto**: cada aspecto recebe uma pontuação de 0 a 100 com base no tipo de aspecto, no peso dos planetas envolvidos (planetas lentos tocando pontos pessoais pesam mais; Ascendente/MC/Quíron têm peso extra), na proximidade do orbe e em retrogradação. É uma heurística do próprio sistema, não um conceito astrológico padronizado — serve para priorizar o que olhar primeiro.
- **Aplicando/separando e retrogradação**: cada aspecto indica se está se formando ou se dissipando, e se o planeta em trânsito está retrógrado no momento.
- **Exportar para IA**: um botão copia (e mostra em texto) o mapa natal, as posições em trânsito e os aspectos filtrados/ordenados, prontos para colar num assistente de IA e pedir interpretação.

## Como usar

1. Abra o arquivo `transitos-astrologicos.html` em qualquer navegador (não precisa de internet, exceto para a busca de cidade).
2. Preencha os dados de nascimento (data é obrigatória; hora, fuso e localização são opcionais, mas sem eles Ascendente e Casas não são calculados). Ou importe um JSON salvo de uma sessão anterior.
3. Clique em **Calcular mapa natal**.
4. Escolha data única ou intervalo, preencha e clique em **Calcular trânsitos**.
5. Use os filtros para focar no que interessa, e o botão **Copiar para IA interpretar** para levar o resultado a uma IA.

## Precisão e limitações

- Posições planetárias: elementos orbitais keplerianos (válidos ~1900–2100, precisão de poucos minutos de arco). Lua: série de termos periódicos (~1 minuto de arco).
- Quíron: elementos osculadores fixos (sem taxas seculares de precessão do nó/periélio) — boa precisão entre ~2000–2050, com erro crescente fora desse intervalo, já que sua órbita de centauro é perturbada por Saturno e Júpiter.
- Ascendente, Meio do Céu e casas: fórmulas padrão de tempo sideral. Placidus falha (por definição matemática, não por bug) em latitudes muito próximas dos polos.
- Nenhum sistema aqui substitui um software de referência (Swiss Ephemeris, Astro.com etc.) para decisões finas perto de uma cúspide, nem substitui a leitura qualitativa de um astrólogo.

## Stack

HTML + CSS + JavaScript puro, sem dependências externas — exceto a chamada opcional à API pública do Nominatim (OpenStreetMap) para a busca de cidade.

## Licença

Projeto pessoal — adicione a licença de sua preferência caso for tornar o repositório público.
