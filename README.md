# 🏁 O CAMPEÃO — Simulador de Carreira na F1
 
> Roube atributos dos craques, saia do kart e descubra se você consegue chegar ao topo da Fórmula 1.
 
**O CAMPEÃO** é um simulador de carreira de automobilismo que roda direto no navegador, em um único arquivo HTML, sem dependências e sem build. Você monta seu piloto sorteando cartas de pilotos reais e lendas, constrói uma trajetória do kart até a F1 e tenta entrar para a história.
 
> ⚠️ **Projeto feito para diversão.** Resultados, notas (OVR) e negociações são fictícios e não têm qualquer relação oficial com a FIA, a Fórmula 1 ou os pilotos citados.
 
---
 
## ✨ Principais recursos
 
- **Draft de atributos:** gire 8 vezes, "roube" um atributo de cada piloto sorteado e monte o seu perfil.
- **Três tipos de carta:** pilotos do grid atual, **Lendas** históricas (douradas) e cartas **PRIME**, versões no auge de grandes nomes (vermelhas, raras).
- **Carreira completa:** Kart → F4 → F3 → F2 → F1, com idades mínimas da FIA aplicadas.
- **Promoção obrigatória:** campeões das categorias de base precisam subir (desde que tenham idade).
- **Mercado de pilotos dinâmico:** a CPU evolui, envelhece, assina contratos, troca de equipe e se aposenta.
- **Evolução dos carros:** ordem de forças baseada nas construtoras atuais, com limite de testes aerodinâmicos e **novos regulamentos** a cada poucos anos.
- **Negociação de contrato:** escolha duração, metas (vitórias, pódios, título) e exija o salário que quiser, sujeito às consequências.
- **Reputação, patrocínios e pilotos pagantes:** o que você faz na pista muda as propostas que recebe.
- **Eventos de decisão:** escolhas arriscadas com roleta de resultado.
- **Imprensa:** manchetes que acompanham a sua carreira e o paddock.
- **11 níveis de legado:** de "Piloto comum" até **O CAMPEÃO**.
- **Cartão final em PNG** para salvar e compartilhar.
- **Ranking local** das melhores carreiras e **save automático**.
---
 
## 🎮 Como jogar
 
1. Digite o **nome**, escolha um **número (1–99)** e a **nacionalidade** do seu piloto.
2. Clique em **NOVO JOGO** e faça o **draft**: em cada giro, escolha qual atributo do piloto sorteado você quer levar. Você tem **2 trocas de piloto** disponíveis.
3. Com o perfil completo, **inicie a carreira** e escolha entre as propostas de equipes de kart (quanto melhor seu perfil, melhores as propostas).
4. A cada temporada você vive três momentos: **abertura**, **metade do campeonato** (com um evento de decisão) e **decisão do título**.
5. No fim do ano, escolha a proposta do mercado, negocie o contrato e siga subindo.
6. A carreira termina por idade ou desempenho. Veja seu nível final e salve o cartão.
### Os 8 atributos
 
| Atributo | Papel na simulação |
|---|---|
| Qualificação | Define o grid de largada |
| Ritmo de corrida | Peso principal do desempenho do piloto na prova |
| Largada | Bônus nas primeiras posições |
| Ultrapassagem | Bônus maior para quem larga mais atrás |
| Chuva | Bônus em corridas molhadas |
| Gestão de pneus | Bônus em corridas longas (não em sprints) |
| Consistência | Reduz a aleatoriedade dos resultados |
| Mentalidade | Bônus nas corridas decisivas do fim da temporada |
 
O **OVR** do piloto é calculado a partir do potencial (média dos atributos) e de um **fator de idade**: jovens ainda não renderam 100%, e veteranos sentem o peso dos anos.
 
---
 
## 🧠 Regras e lógica
 
- **Corrida:** o carro pesa cerca de 50% no resultado, o piloto cerca de 30%, além de qualificação, bônus de atributos e sorte. Há **quebras e acidentes**, mais prováveis em carros piores.
- **Calendário:** Kart 10 corridas, F4 e F3 16 corridas, F2 14 corridas e F1 com 24 GPs mais 6 sprints.
- **Idade mínima de promoção:** F4 (15), F3 (16), F2 (17) e F1 (18). Campeão sem idade para subir fica mais um ano.
- **Saltos de categoria:** bons resultados com patrocínio ou *breakout* podem render um convite para pular uma divisão.
- **Fim de carreira:** nas categorias de base, aos 23 anos; na F1, a partir dos 41, após duas temporadas ruins seguidas ou por aposentadoria sorteada para veteranos.
- **Determinismo:** o jogo usa um gerador pseudoaleatório com **seed** (exibida no canto superior direito). Mesma seed e mesmas escolhas dão os mesmos resultados.
---
 
## 🏆 Níveis de legado
 
1. Piloto comum
2. Sensação de uma temporada
3. Piloto de ponta
4. Vencedor de GPs
5. Campeão do mundo
6. Bicampeão
7. Tricampeão
8. Lenda do grid
9. Top 5 de todos os tempos
10. Sempre citado no debate GOAT
11. **O CAMPEÃO**
---
 
## 🚀 Como executar
 
Não há instalação nem etapa de build.
 
```bash
# Opção 1: abrir direto no navegador
abrir index.html
 
# Opção 2: servir localmente (opcional)
python3 -m http.server 8000
# acesse http://localhost:8000
```
 
> As fontes (**Inter** e **Space Grotesk**) são carregadas do Google Fonts. Sem internet, o jogo funciona normalmente com as fontes de fallback.
 
O projeto também pode ser publicado em qualquer hospedagem estática (GitHub Pages, Netlify, Vercel etc.).
 
---
 
## 🗂️ Estrutura
 
```
.
├── index.html   # HTML, CSS e JavaScript em um único arquivo
├── image.png    # Favicon
└── README.md
```
 
Dentro do `index.html`, o código está organizado em blocos:
 
| Bloco | Conteúdo |
|---|---|
| Dados | `CUR` (grid atual), `L` (Lendas), `PRIME`, `F1T` (equipes de F1), `SR` (séries de base) |
| Draft | `spin()`, `dr()` |
| Simulação | `sim_races()`, `carsStep()`, `market()`, `seasonEnd()` |
| Contratos | `offers()`, `sbase()`, `fixNeg()`, `signC()`, `evalCon()` |
| Interface | `draw()`, `finish()`, `lb()` |
 
---
 
## 💾 Armazenamento local
 
O jogo usa o `localStorage` do navegador:
 
| Chave | Uso |
|---|---|
| `tc_save` | Save automático da carreira em andamento (botão **CONTINUAR CARREIRA**) |
| `tc_best` | Ranking local com as 10 melhores carreiras |
 
Nenhum dado é enviado para servidores.
 
---
 
## 🛠️ Personalização
 
Quase tudo é editável direto nos arrays de dados do início do script:
 
- **Atualizar o grid:** edite `CUR`. Cada linha segue `[nome, bandeira, OVR, ritmo, qualificação, gestão, consistência, idade, índice da equipe]`.
- **Adicionar Lendas ou cartas PRIME:** inclua novos itens em `L` ou `PRIME` com os 8 atributos na ordem de `AT`.
- **Ajustar equipes e força dos carros:** edite `F1T` (F1) e `SR[n].T` (categorias de base).
- **Balanceamento:** os pesos da corrida ficam em `sim_races()` e as probabilidades das cartas em `spin()`.
- **Tema visual:** variáveis CSS no `:root` (`--accent`, `--g`, `--bg` etc.).
---
 
## 🧰 Tecnologias
 
- HTML5, CSS3 (Grid, Flexbox, variáveis CSS, animações)
- JavaScript puro (ES6+), sem frameworks
- Canvas API para gerar o cartão final em PNG
- `localStorage` para persistência
---
 
## 📄 Aviso legal
 
Este é um projeto de fã, sem fins lucrativos. Nomes de pilotos, equipes e marcas pertencem aos seus respectivos donos. Todos os valores, resultados e eventos são fictícios e criados apenas para entretenimento.
 
---
 
Feito com 🏎️ e paixão por automobilismo.
