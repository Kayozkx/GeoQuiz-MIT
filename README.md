![Banner](assets/banner.png)
# 🌎 GeoQuiz Bandeiras
![MIT App Inventor](https://img.shields.io/badge/Engine-MIT%20App%20Inventor-blue)
![Plataforma](https://img.shields.io/badge/Plataforma-Android-green)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)

## 📋 Índice

- [Sobre o App](#-sobre-o-app)
- [Telas do Aplicativo](#-telas-do-aplicativo)
  - [Tela 1 — Menu Principal](#tela-1--menu-principal)
  - [Tela 2 — Quiz](#tela-2--quiz)
  - [Tela 3 — Modo Estudo](#tela-3--modo-estudo)
  - [Tela 4 — Divisões Territoriais](#tela-4--divisões-territoriais)
- [Países Incluídos](#-países-incluídos)
- [Como Replicar](#-como-replicar)
- [Importar o Projeto](#-importar-o-projeto)
- [O que Aprendi](#-o-que-aprendi)
- [Autor](#️-autor)

---

## 📱 Sobre o App

GeoQuiz Bandeiras é um aplicativo educativo para Android que testa seus conhecimentos sobre os países da América do Sul através de um quiz de bandeiras com cronômetro, e permite aprender sobre cada país no Modo Estudo com mapas, áudios e informações detalhadas.

**Plataforma:** Android
**Ferramenta:** MIT App Inventor
**Telas:** 4
**Países:** 12 países da América do Sul

---

## 🎮 Como Usar

1. Abra o app no celular
2. Na tela inicial escolha entre **Quiz** ou **Modo Estudo**
3. No **Quiz** observe a bandeira exibida e escolha o país correto entre as 4 opções antes do tempo de 15 segundos acabar
4. No **Modo Estudo** navegue entre os países com as setas e explore informações como capital, população, idioma e curiosidades
5. Use o botão **Mapa** para ver a localização da capital e **Saiba Mais** para abrir a Wikipedia do país
6. No **Modo Estudo** acesse também as divisões territoriais de cada país pelo botão **Divisões**

---

![Demo](assets/demo.gif)

Aplicativo educativo desenvolvido no MIT App Inventor para Android. Teste seus conhecimentos sobre os países da América do Sul através de um quiz de bandeiras, e aprenda sobre cada país no Modo Estudo.

> Projeto pessoal desenvolvido para fins de aprendizado e testes.

---

## 📱 Telas do Aplicativo

### Tela 1 — Menu Principal

Tela inicial com duas opções de acesso.

![Menu Principal](assets/tela_menu.png)

#### Blocos — Menu Principal

Os blocos da tela inicial são simples: cada botão abre uma tela diferente.

- **Botão ENTRAR** → abre a `Screen2` (Quiz)
- **Botão MODO ESTUDO** → abre a `Screen3` (Modo Estudo)

![Blocos Menu](assets/blocks_menu.png)

---

### Tela 2 — Quiz

O quiz apresenta 12 perguntas sobre bandeiras dos países da América do Sul. Cada pergunta tem 4 opções de resposta e um contador regressivo de 15 segundos.

![Tela Quiz](assets/tela_quiz.png)

#### Funcionalidades
- ⏱️ **Tempo:** 15 segundos por pergunta com barra de progresso visual
- 🏆 **Pontuação:** exibida em tempo real
- 💡 **Dica:** revela uma curiosidade sobre o país
- 👁️ **Revelar:** mostra a resposta correta
- ⏭️ **Pular:** avança para a próxima pergunta sem pontuar
- 🔙 **Voltar:** retorna ao menu principal

#### Blocos — Quiz

Os blocos desta tela controlam toda a lógica do quiz:

- **Listas de dados:** imagens das bandeiras, perguntas, respostas corretas e opções embaralhadas são armazenadas em listas globais
- **CarregarPergunta:** função principal que sorteia uma bandeira aleatória, define as 4 opções de resposta e inicia o timer
- **Clock (Timer):** a cada tick decrementa o tempo; quando chega a zero passa automaticamente para a próxima pergunta
- **VerificarResposta:** compara a opção clicada com a resposta correta, atualiza a pontuação e muda a cor do botão (verde = acerto, vermelho = erro)
- **Revelar / Dica / Pular:** blocos auxiliares que expõem informações ou avançam o índice da pergunta
- **Fim do Quiz:** quando as 12 perguntas acabam, exibe um dialog com a pontuação final e opções de jogar novamente ou voltar ao menu

![Blocos Quiz](assets/blocks_quiz.png)

---

### Tela 3 — Modo Estudo

Permite aprender sobre cada país da América do Sul com informações detalhadas, mapa interativo e recursos externos.

![Modo Estudo](assets/tela_estudo.png)
![Modo Estudo — informações](assets/tela_estudo_info.png)

#### Informações exibidas por país
- País, Capital, Continente
- População, Área, Idioma
- Moeda, Curiosidade, Significado da bandeira
- Estados/Divisões territoriais

#### Funcionalidades
- 🔊 **Áudio:** pronuncia o nome do país no idioma local
- 📍 **Localização:** exibe no mapa a posição do país na América do Sul
- 🗺️ **Mapa:** abre o mapa com as coordenadas exatas da capital
- 🌐 **Saiba Mais:** abre a página da Wikipedia do país
- 📌 **Google Maps:** abre o Google Maps com as coordenadas da capital
- ➡️ **Divisões:** navega para a Tela 4 com as divisões territoriais do país
- ◀️▶️ **Navegação:** botões para avançar e voltar entre os países

#### Blocos — Modo Estudo

- **Listas globais:** cada país tem suas próprias listas de dados (nome, capital, população, área, idioma, moeda, curiosidade, significado, estados, coordenadas latitude/longitude, links Wikipedia)
- **CarregarPais:** função central que carrega todos os dados do índice atual e preenche todos os labels da tela
- **Mapa:** usa o componente Map do MIT App Inventor com latitude e longitude de cada capital para posicionar o marcador
- **Anterior / Próximo:** decrementam ou incrementam o índice global e chamam CarregarPais
- **Áudio:** usa o componente Sound para tocar o arquivo mp3 com a pronúncia do nome do país
- **ActivityStarter (Wikipedia):** abre o navegador com a URL da Wikipedia do país usando `android.intent.action.VIEW`
- **ActivityStarter (Google Maps):** monta a URL `https://maps.google.com/?q=latitude,longitude` e abre no Maps
- **Botão Divisões:** passa o índice atual para a Screen4 via `open another screen with start value`

![Blocos Modo Estudo](assets/blocks_estudo.png)

---

### Tela 4 — Divisões Territoriais

Exibe as divisões administrativas (estados, departamentos, províncias ou regiões) de cada país com suas respectivas bandeiras.

![Tela Divisões](assets/tela_divisoes.png)

#### Funcionalidades
- 🗺️ Mapa do país com divisões coloridas
- 📋 Lista de todos os estados/departamentos/províncias
- 🏳️ **Botão Bandeiras:** alterna entre o mapa padrão e o mapa com as bandeiras de cada divisão territorial
- ◀️▶️ Navegação entre países
- 🔙 **Voltar:** retorna ao Modo Estudo

#### Blocos — Divisões

- **Listas globais:** listas de divisões, bandeiras das divisões e imagens dos mapas por país
- **carregarestado:** função principal que carrega o mapa, nome do país, lista de estados e a bandeira de fundo conforme o índice
- **Botão Bandeiras:** alterna a variável `mostrandobands` entre `true` e `false`, trocando a imagem exibida entre mapa normal e mapa com bandeiras das divisões
- **Anterior / Próximo:** navegação entre países com verificação de limite de lista
- **Voltar:** retorna para a Screen3 (Modo Estudo)

![Blocos Divisões](assets/blocks_divisoes.png)

---

## 🌍 Países incluídos

Todos os 12 países da América do Sul:

| País | Capital |
|------|---------|
| 🇧🇷 Brasil | Brasília |
| 🇦🇷 Argentina | Buenos Aires |
| 🇨🇱 Chile | Santiago |
| 🇺🇾 Uruguai | Montevidéu |
| 🇵🇾 Paraguai | Assunção |
| 🇧🇴 Bolívia | Sucre / La Paz |
| 🇵🇪 Peru | Lima |
| 🇪🇨 Equador | Quito |
| 🇨🇴 Colômbia | Bogotá |
| 🇻🇪 Venezuela | Caracas |
| 🇬🇾 Guiana | Georgetown |
| 🇸🇷 Suriname | Paramaribo |

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Uso |
|-----------|-----|
| MIT App Inventor | Desenvolvimento do app |
| Android | Plataforma alvo |
| Google Maps | Visualização das capitais via ActivityStarter |
| Wikipedia | Links de saiba mais por país via ActivityStarter |
| Sound | Reprodução de áudio com pronúncia dos países |

---

## 🔁 Como replicar

1. Acesse [MIT App Inventor](https://appinventor.mit.edu)
2. Crie um novo projeto
3. Recrie as 4 telas conforme as imagens e blocos documentados acima
4. Adicione os assets (imagens das bandeiras, mapas, áudios) na aba **Media**
5. Monte os blocos seguindo a documentação de cada tela
6. Compile e teste no celular via **MIT AI2 Companion** ou gerando o APK

---

## 📦 Importar o Projeto

Caso prefira, baixe o arquivo `GeoQuizBandeiras.aia` na seção [Releases](../../releases) e importe diretamente no MIT App Inventor em vez de recriar do zero:

Projects → Import project (.aia)

---

## 📚 O que Aprendi

- Organização de listas globais e manipulação de dados no MIT App Inventor
- Criação de sistemas de quiz com timer e pontuação
- Integração com Google Maps e Wikipedia via ActivityStarter
- Uso do componente Map para exibir coordenadas geográficas
- Reprodução de áudio com o componente Sound
- Navegação entre telas passando dados via start value
- Documentação técnica de projetos de programação em blocos

---

## ✏️ Autor

Desenvolvido por **Kayozkx**  
Projeto educativo pessoal — América do Sul

> Desenvolvido entre 30 de abril de 2026 e 04 de junho de 2026.

---

> Este repositório documenta a lógica e estrutura do app para quem quiser replicar ou aprender com o projeto.
